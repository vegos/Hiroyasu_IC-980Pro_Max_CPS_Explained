# Hiroyasu IC-980Pro Max CPS (8110) Adjustment Menu – Translation & Function Reference

![Original](images/CPS_Adjustment.png)  

![Translated](images/CPS_Adjustment_Translated.png)  

![Translated](images/CPS_Adjustment_NoText.png)  

---  

## RF / Audio Parameters

| Chinese | English | Function |
|--------|--------|----------|
| 宽带频偏-U | Wideband Deviation Offset (UHF) | Sets FM deviation level for UHF in wide mode |
| 宽带频偏-V | Wideband Deviation Offset (VHF) | Sets FM deviation level for VHF in wide mode |
| CTC频偏 | CTCSS Deviation Offset | Adjusts deviation of CTCSS tone |
| DCS频偏 | DCS Deviation Offset | Adjusts deviation of DCS signaling |
| MIC增益 | Mic Gain | Controls microphone input level (TX modulation) |
| MIC自动增益 | Mic AGC | Automatic microphone gain control |
| 音量Rx Gain2 | RX Audio Gain | Controls received audio amplification |
| 音量DAC Gain | AF DAC Gain | Controls audio output level (speaker/AF out) |
| Glitch | Glitch Filter | Filters short noise spikes/interference |
| 测频距离 | Frequency Step | Frequency measurement/scan step resolution |

---

## Voltage & Audio

| Chinese | English | Function |
|--------|--------|----------|
| 最高电压 | Max Voltage | Maximum operating voltage |
| 关机电压 | Low Voltage Cutoff | Voltage threshold for automatic shutdown |
| 音频功放电平 | AF Power Level | Audio amplifier output level |
| 开机喇叭延时(ms) | Power-on Speaker Delay (ms) | Delay before speaker activates on startup |

---

## Monitoring / Live Values

| Chinese | English | Function |
|--------|--------|----------|
| 信号强度 | Signal Strength | Received signal strength (RSSI) |
| 噪声强度 | Noise Level | Background noise level |
| 电压值 | Voltage Value | Current supply voltage |
| 声控值 | VOX Level | VOX activation threshold |
| 读取机子状态 | Read Radio Status | Reads real-time radio status |

---

## Squelch / Noise Threshold

| Chinese | English | Function |
|--------|--------|----------|
| 噪声阈门 | Noise Threshold Level | Defines squelch opening threshold |
| 低-开 | Low Open | Squelch open threshold (low level) |
| 低-关 | Low Close | Squelch close threshold (low level) |
| 中-开 | Mid Open | Squelch open threshold (mid level) |
| 中-关 | Mid Close | Squelch close threshold (mid level) |
| 高-开 | High Open | Squelch open threshold (high level) |
| 高-关 | High Close | Squelch close threshold (high level) |
| 宽带 | Wide | Applies to wideband FM |
| 窄带 | Narrow | Applies to narrowband FM |

---

## Band Ranges

| Chinese | English | Function |
|--------|--------|----------|
| U段-扩频范围 | UHF Frequency Range (Extended) | Defines extended operating range UHF (Unlocked) |
| U段-收频范围 | UHF Receive Range | Defines receive frequency range |
| V段-扩频范围 | VHF Frequency Range (Extended) | Defines extended operating range VHF (Unlocked) |
| V段-收频范围 | VHF Receive Range | Defines receive frequency range (VHF) |
| 最小 | Min | Minimum frequency |
| 最大 | Max | Maximum frequency |

---

## Buttons

| Chinese | English | Function |
|--------|--------|----------|
| 读取 | Read | Read settings from radio |
| 写入 | Write | Write settings to radio |
| 全写 | Write All | Write all parameters to radio |
| 新建 | New | Create new configuration |
| 打开 | Open | Open configuration file |
| 保存 | Save | Save configuration file |

---

![Original](images/CPS_Adjustment_Center.png)  


## APC Power Adjustment Table

| Column | Meaning | Description |
|--------|--------|-------------|
| Freq | Frequency (MHz) | Reference frequency point for calibration |
| High Power | TX High Power Level | Output power setting when radio is in high power mode |
| Low Power | TX Low Power Level | Output power setting when radio is in low power mode |
| RX Tune | RX Gain Calibration | Receiver calibration value (affects sensitivity and alignment) |
| RF Out | RF Drive Level | RF output drive level from the chipset (controls PA drive) |

### Notes:
- Values are frequency-dependent (lookup table behavior)
- Used to shape TX power curve and RX performance across the band
- Incorrect values may affect:
  - Output power
  - Linearity
  - Receiver sensitivity

---

## SQ / Noise Table

| Column | Meaning | Description |
|--------|--------|-------------|
| Freq | Frequency (MHz) | Frequency threshold (applies up to this frequency) |
| SQ | Squelch Level | Base squelch threshold value |
| Noise | Noise Level | Reference noise floor value |
| Narrow SQ | Narrowband Squelch | Squelch threshold when in narrowband mode |
| Narrow Noise | Narrowband Noise | Noise reference for narrowband mode |

### Notes:
- Defines squelch behavior per frequency range
- Implements hysteresis-based squelch control
- Wideband vs Narrowband handled separately
- Affects:
  - When the receiver opens
  - Stability of squelch (no chattering)

---

## General Behavior

- Both tables act as **lookup tables (LUTs)**
- The radio interpolates values between frequency points
- Used for:
  - RF calibration
  - Audio/RF balance
  - Squelch accuracy

---

## ⚠️ Warning

- These are **factory calibration parameters**
- Changing them without measurement equipment may result in:
  - Incorrect TX power
  - Poor modulation
  - Receiver desensitization
  - Unstable squelch behavior
  - Magic Smoke!   

---

## Adjustment Menu Passwords

- ww01  
  The options defined here  
- wwuser  
- wwpd  
- wwband  
  Expand RX/TX frequencies by band (UHF/VHF, Min to Max)  
- wwjxs  
- updated  
- logo  
  Change Logo. Must be bitmap, 16bit  

---

### ⚠️ Important – Backup Before Making Changes

Before modifying any settings in the CPS:

> **Always perform a "Read" from the radio and save the configuration file.**

This ensures you have a full backup of the original (factory or working) settings.

If something goes wrong (e.g. no transmission, abnormal behavior, or misconfiguration), you will be able to:

- Restore the saved file  
- Write it back to the radio  
- Recover normal operation  

⚠️ Skipping this step may leave you without a working configuration, making recovery difficult.

---  

## Tool for memory management (import/export from/to CSV)

You can use the python script provider [here](https://github.com/vegos/Hiroyasu_IC-980Pro_Max) to export to CSV or import channel memories for your radio.  
An easy way to edit/clone/etc memories.  

---

## Author

Antonis Maglaras — ©2026
