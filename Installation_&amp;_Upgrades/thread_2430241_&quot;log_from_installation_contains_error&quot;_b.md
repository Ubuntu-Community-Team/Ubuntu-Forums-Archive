---
title: "&quot;log from installation contains error&quot; but can't see one?"
date: 2019-10-29
forum: Installation &amp; Upgrades
---

### Post by pateksan on 2019-10-29
Hello again,

I've not had any luck with my previous installation (at time of posting this anyway) - [https://ubuntuforums.org/showthread.php?t=2430088](https://ubuntuforums.org/showthread.php?t=2430088)

I've tried reinstalling and got the following:
> The system log from your installation contains an error. The specific
error commonly occurs when there is an issue with the disk to which you
are trying to install Ubuntu. It is recommended that you back up
important data on your disk and investigate the situation. Measures you
might take include checking cable connections for your disks and using
software tools to investigate the health of your hardware.
**The problem is I can't see any details in the log**. The log is here: [https://paste.ubuntu.com/p/K4Wx3drZdz/](https://paste.ubuntu.com/p/K4Wx3drZdz/)

Can someone have a look to see which line in the log has caused the prompt? This might allow me to troubleshoot further.

SMART indicates the drive is likely to fail soon, but that has been the case for a while: the previous three attempts to install linux did not produce the message quoted above.
(FWIM they did all have the booting issue in my other thread above - if you think the booting issue is due to the dodgy drive then please do let me know, I don't mind which thread you respond in).

---

### Post by TheFu on 2019-11-01
Please post the raw SMART data from **smartctl -a** wrapped in code tags so the columns are lined up.

---

### Post by pateksan on 2019-11-05
Thanks TheFu. Please let me know if I should be posting a link to a pastebin instead. Also, I will be doing a bit more research into how much exactly I need to worry about the imminent failure warning, but here it is in the meantime.
```
[COLOR=#000000]smartctl 7.0 2018-12-30 r4883 [x86_64-linux-5.3.0-19-generic] (local build)[/COLOR]Copyright (C) 2002-18, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar Z7K320
Device Model:     HITACHI HTS723232A7A364
Serial Number:    E3834563KUUBWN
LU WWN Device Id: 5 000cca 61df60313
Firmware Version: EC2ZB70R
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Nov  5 23:24:18 2019 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (   45) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  76) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   084   084   062    Pre-fail  Always       -       15007894
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   253   253   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   098   098   000    Old_age   Always       -       3626
  5 Reallocated_Sector_Ct   0x0033   001   001   005    Pre-fail  Always   FAILING_NOW 0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   090   090   000    Old_age   Always       -       4529
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       3033
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       2558918775
193 Load_Cycle_Count        0x0012   063   063   000    Old_age   Always       -       379259
194 Temperature_Celsius     0x0002   171   171   000    Old_age   Always       -       35 (Min/Max 2/46)
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       2518
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       18
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
Warning: ATA error count 65535 inconsistent with error log pointer 3

ATA Error Count: 65535 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 65535 occurred at disk power-on lifetime: 4529 hours (188 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 5f 39 18 42 0e  Error: IDNF at LBA = 0x0e421839 = 239212601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 90 78 00 db 42 40 08      01:24:53.374  WRITE FPDMA QUEUED
  61 90 70 00 da 42 40 08      01:24:53.372  WRITE FPDMA QUEUED
  61 98 28 00 18 42 40 08      01:24:53.265  WRITE FPDMA QUEUED
  61 98 20 00 d1 42 40 08      01:24:53.265  WRITE FPDMA QUEUED
  61 70 18 00 d2 42 40 08      01:24:53.265  WRITE FPDMA QUEUED

Error 65534 occurred at disk power-on lifetime: 4529 hours (188 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 5f 39 18 42 0e  Error: IDNF at LBA = 0x0e421839 = 239212601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 88 68 00 df 42 40 08      01:24:51.217  WRITE FPDMA QUEUED
  61 50 60 00 dc 42 40 08      01:24:51.215  WRITE FPDMA QUEUED
  61 88 58 00 d9 42 40 08      01:24:51.205  WRITE FPDMA QUEUED
  61 90 50 00 d8 42 40 08      01:24:51.204  WRITE FPDMA QUEUED
  61 90 48 00 d7 42 40 08      01:24:51.202  WRITE FPDMA QUEUED

Error 65533 occurred at disk power-on lifetime: 4529 hours (188 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 5f 39 18 42 0e  Error: IDNF at LBA = 0x0e421839 = 239212601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 d0 30 fb 9e 40 08      01:24:49.108  WRITE FPDMA QUEUED
  61 88 b8 00 cf 42 40 08      01:24:49.107  WRITE FPDMA QUEUED
  61 90 58 00 1a 42 40 08      01:24:49.085  WRITE FPDMA QUEUED
  61 88 50 00 1b 42 40 08      01:24:49.084  WRITE FPDMA QUEUED
  61 88 48 00 c7 42 40 08      01:24:49.084  WRITE FPDMA QUEUED

Error 65532 occurred at disk power-on lifetime: 4529 hours (188 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 5f 39 18 42 0e  Error: IDNF at LBA = 0x0e421839 = 239212601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 88 b0 00 ce 42 40 08      01:24:47.034  WRITE FPDMA QUEUED
  61 b0 a8 00 cd 42 40 08      01:24:47.033  WRITE FPDMA QUEUED
  61 90 a0 00 cc 42 40 08      01:24:47.029  WRITE FPDMA QUEUED
  61 98 98 00 cb 42 40 08      01:24:47.028  WRITE FPDMA QUEUED
  61 88 90 00 ca 42 40 08      01:24:47.025  WRITE FPDMA QUEUED

Error 65531 occurred at disk power-on lifetime: 4529 hours (188 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 5f 39 18 42 0e  Error: IDNF at LBA = 0x0e421839 = 239212601

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 a8 18 00 19 42 40 08      01:24:44.961  WRITE FPDMA QUEUED
  61 e0 10 00 1c 42 40 08      01:24:44.961  WRITE FPDMA QUEUED
  61 90 08 00 1a 42 40 08      01:24:44.961  WRITE FPDMA QUEUED
  61 88 00 00 1b 42 40 08      01:24:44.961  WRITE FPDMA QUEUED
  61 98 f8 00 c0 42 40 08      01:24:44.961  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk. [COLOR=#000000]If Selective self-test is pending on power-up, resume after 0 minute delay.[/COLOR]
```

---

### Post by TheFu on 2019-11-05
Unplug this drive NOW!@!@!@@@!@!#!@!!!!!
You have data loss already.  The only thing this drive should be used for, if that is even possible, is to be cloned to another HDD so you can attempt data recovery.  Do not use it for any other reason. Do not boot on this disk. Boot from a Try Ubuntu flash "thumb drive".
```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   084   084   062    Pre-fail  Always       -       15007894
  5 Reallocated_Sector_Ct   0x0033   001   001   005    Pre-fail  Always   FAILING_NOW 0  
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       2518
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       18
```

Those are why I say you should unplug NOW.

There is good news. It appears that the SATA cable is fine.

This specific disk should be considered dead.

---

