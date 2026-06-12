---
title: "Install chrashes!"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by erikja on 2013-02-08
Hi.

Would install ubuntu 12.04.1 LTS.

I have issues with the install.

It chrashes as the install is nearly finished.

I can fine get ubuntu up running if I choose the live test "Try Ubuntu".

ASUS P5Q Deluxe 4G of RAM, NVIDIA Gefocre 7300 LE. 32bit

What to do ?.

/Erik

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by erikja on 2013-02-08
@ahallubuntu

Thank you for your reply.

I have a running Windows 7 Ultimate 32bit on this computer, and it has never failed.

Why this ?.

I have a caddy on this computer, that gives me the option to qucikly change HDD's.

That is what I did when starting up install Ubuntu.

I will run through what you suggests, and will be back here with informations.

/Erik

---

### Post by erikja on 2013-02-09
@ahallubuntu

I went through the tests.

RAM test went ok, but the SMART test showed errors.

They are here:

```
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD800AAJS-00B4A0
Serial Number:    WD-WCAT21330804
LU WWN Device Id: 5 0014ee 1abda4397
Firmware Version: 01.03A01
User Capacity:    80,026,361,856 bytes [80.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Feb  9 06:42:11 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 2580) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  34) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       58
  3 Spin_Up_Time            0x0027   156   155   021    Pre-fail  Always       -       3191
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       134
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       256
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       132
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       54
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       134
194 Temperature_Celsius     0x0022   113   089   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       5
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       6
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       8

SMART Error Log Version: 1
Warning: ATA error count 52 inconsistent with error log pointer 1

ATA Error Count: 52 (device log contains only the most recent five errors)
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

Error 52 occurred at disk power-on lifetime: 143 hours (5 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 2a 8b c2 e7  Error: UNC at LBA = 0x07c28b2a = 130190122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 f3 8a c2 07 00      01:19:56.281  READ DMA
  ca 00 18 8b 01 60 00 00      01:19:56.281  WRITE DMA
  ca 00 08 0b 01 60 00 00      01:19:56.281  WRITE DMA
  ca 00 08 c3 00 60 00 00      01:19:56.281  WRITE DMA
  ca 00 08 a3 00 60 00 00      01:19:56.281  WRITE DMA

Error 51 occurred at disk power-on lifetime: 143 hours (5 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 2a 8b c2 e7  Error: UNC at LBA = 0x07c28b2a = 130190122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 f3 8a c2 07 00      01:19:53.906  READ DMA
  c8 00 01 00 00 00 00 00      01:19:53.906  READ DMA
  c8 00 40 f3 8a c2 07 00      01:19:51.512  READ DMA
  c8 00 01 00 00 00 00 00      01:19:51.491  READ DMA
  c8 00 40 f3 8a c2 07 00      01:19:49.104  READ DMA

Error 50 occurred at disk power-on lifetime: 143 hours (5 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 2a 8b c2 e7  Error: UNC at LBA = 0x07c28b2a = 130190122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 f3 8a c2 07 00      01:19:51.512  READ DMA
  c8 00 01 00 00 00 00 00      01:19:51.491  READ DMA
  c8 00 40 f3 8a c2 07 00      01:19:49.104  READ DMA
  ca 00 08 0b 00 5e 00 00      01:19:48.944  WRITE DMA
  ca 00 08 1b 00 5e 00 00      01:19:48.944  WRITE DMA

Error 49 occurred at disk power-on lifetime: 143 hours (5 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 2a 8b c2 e7  Error: UNC at LBA = 0x07c28b2a = 130190122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 f3 8a c2 07 00      01:19:49.104  READ DMA
  ca 00 08 0b 00 5e 00 00      01:19:48.944  WRITE DMA
  ca 00 08 1b 00 5e 00 00      01:19:48.944  WRITE DMA
  ca 00 48 4b 00 5f 00 00      01:19:48.944  WRITE DMA
  c8 00 08 eb 48 2b 00 00      01:19:48.569  READ DMA

Error 48 occurred at disk power-on lifetime: 143 hours (5 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 2a 8b c2 e7  Error: UNC at LBA = 0x07c28b2a = 130190122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 f3 8a c2 07 00      01:15:15.218  READ DMA
  c8 00 40 3d 0d 05 00 00      01:15:15.217  READ DMA
  c8 00 40 bd 0d 05 00 00      01:15:15.209  READ DMA
  c8 00 08 9b f6 07 00 00      01:15:15.208  READ DMA
  c8 00 18 6b f7 07 00 00      01:15:15.208  READ DMA

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
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

I also attached photos.

What do you say to this ?.

---

### Post by erikja on 2013-02-09
I installed another HDD.

I ran the gsmartcontrol on it, and it showed ok.

Then I installed again.

I got the same chrash as before.

I have checked the md5 before I made the CD ready.

Now I made a USB bootdisk, and all went well.

Probably it might have been something with my DVD drive, I don't know.

Thanks for your help :-)

---

### Post by dino99 on 2013-02-09
first error : crash (not chrash)

before installation, load windows to clean the system (ccleaner) then defrag. Then load the formatting tool to see about possible warnings/errors.

When burning, keep in mind to always use the slowest speed to avoid burning errors (k3b is a good choice).

---

### Post by erikja on 2013-02-09
@dino99

Many thanks for your advices :D

/Erik

---

