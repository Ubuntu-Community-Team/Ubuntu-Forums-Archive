---
title: "SATA errors"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by jeremiah.bloogs99 on 2008-08-28
I replaced a failing SATA harddrive with a new one, and now have two drives that fail apparently the same way. However, at the moment I am keeping an open mind about whether the symptoms are related. There is a lot of error messages from the new 1TB WD drive, such as

[24256.369607] Buffer I/O error on device sdb1, logical block 21499352
[24256.369607] lost page write due to I/O error on sdb1
[24256.369607] Buffer I/O error on device sdb1, logical block 21499353
[24256.369607] lost page write due to I/O error on sdb1

(.....)

[24300.532219] ata4.00: status: { DRDY }
[24300.532227] ata4.00: cmd 61/08:68:ef:0d:20/00:00:02:00:00/40 tag 13 ncq 4096 out
[24300.532229]          res 40/00:7c:ff:0d:20/00:00:02:00:00/40 Emask 0x1 (device error)
[24300.532239] ata4.00: status: { DRDY }
[24300.532247] ata4.00: cmd 61/08:70:f7:0d:20/00:00:02:00:00/40 tag 14 ncq 4096 out
[24300.532248]          res 40/00:7c:ff:0d:20/00:00:02:00:00/40 Emask 0x1 (device error)
[24300.532259] ata4.00: status: { DRDY }
[24300.532267] ata4.00: cmd 61/16:78:ff:0d:20/00:00:02:00:00/40 tag 15 ncq 11264 out
[24300.532269]          res 40/00:7c:ff:0d:20/00:00:02:00:00/40 Emask 0x1 (device error)
[24300.532279] ata4.00: status: { DRDY }
[24300.532289] ata4: hard resetting link
[24307.064406] ata4: link is slow to respond, please be patient (ready=0)
[24310.536423] ata4: softreset failed (device not ready)
[24310.536443] ata4: hard resetting link
[24317.068941] ata4: link is slow to respond, please be patient (ready=0)
[24320.541469] ata4: softreset failed (device not ready)
[24320.541488] ata4: hard resetting link

Smartctl claims that the drive passes, though I suppose it would not know about interface errors. Selftests do not reveal any evidence of a serious failure. The drive is very slow, but it is possible to eventually format and use a small partition on it (10G). An attempt to format the whole TB results in mkfs saying "ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir" I am using the M2A-VM board (64 bit AMD, 2G of RAM) that has had issues with SATA controllers in the past, though they are supposedly resolved in the current kernel. 

I have tried booting with noapic, nolapic, pci=nomsi, irqpoll, and probably other options. I tried different versions of Ubuntu including Gutsy, latest Heron and an alpha version of Intrepid. Some were 32-bit and some 64-bit. I also tried stable Debian. It seems the error recovery is somewhat faster under Intrepid but lots of errors still get logged and the symptoms are basically the same under all versions of Linux I tried. I don't have a copy of Windows I could test with.

The computer is less than a year old and worked reliably for months before the failures began. However, I may be using a different version of Ubuntu now. I swapped the SATA cables and SATA ports without any effect. The SATA DVD drive works fine.

So, am I exceptionally unlucky to have bought a broken replacement drive and should I try to have it exchanged even though its smart status is PASSED? What else can I try to either fix or diagnose the problem. I will be most grateful for any suggestions.

---

### Post by mrsteveman1 on 2008-08-28
Smart can pass a test even if there are uncorrectable blocks on the platters.

Read the values for the smart data and see if there are any pending sectors or offline uncorrectables, also look at the ECC errors. In fact post it all if you can :D

---

### Post by jeremiah.bloogs99 on 2008-08-28
Here is the whole SMART data as requested. There is now a failed extended offline test. The SMART faq [http://smartmontools.sourceforge.net/faq.html](http://smartmontools.sourceforge.net/faq.html) suggests this is "fine", and that there may be good reasons for it. I am inclined to agree it is nothing to do with the slowness I am seeing which occurs also on writes. Once again, many thanks for any suggestions!

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD1000FYPS-01ZKB0
Serial Number:    WD-WCASJ1848803
Firmware Version: 02.01B01
User Capacity:    1*000*204*886*016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Aug 28 13:23:51 2008 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (26400) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   253   207   021    Pre-fail  Always       -       2800
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       67
  5 Reallocated_Sector_Ct   0x0033   169   169   140    Pre-fail  Always       -       244
  7 Seek_Error_Rate         0x000e   199   197   000    Old_age   Always       -       22
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       18
 10 Spin_Retry_Count        0x0012   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       62
192 Power-Off_Retract_Count 0x0032   197   197   000    Old_age   Always       -       2637
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2810
194 Temperature_Celsius     0x0022   125   103   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   191   190   000    Old_age   Always       -       9
197 Current_Pending_Sector  0x0012   195   195   000    Old_age   Always       -       849
198 Offline_Uncorrectable   0x0010   195   195   000    Old_age   Offline      -       843
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   191   191   000    Old_age   Offline      -       971

SMART Error Log Version: 1
ATA Error Count: 60 (device log contains only the most recent five errors)
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

Error 60 occurred at disk power-on lifetime: 16 hours (0 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff 58 70 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 02 00 ff 58 70 74 08      00:04:12.238  READ FPDMA QUEUED
  60 20 00 7f 88 c3 73 08      00:04:12.237  READ FPDMA QUEUED
  60 14 00 3f 00 00 00 08      00:04:12.222  READ FPDMA QUEUED
  60 08 00 00 02 00 00 08      00:04:11.768  READ FPDMA QUEUED
  60 28 00 b8 01 00 00 08      00:04:11.767  READ FPDMA QUEUED

Error 59 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 02 ff 58 70 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 20 6c 70 74 08      00:09:58.723  READ FPDMA QUEUED
  60 08 00 b0 6c 70 74 08      00:09:58.723  READ FPDMA QUEUED
  60 08 00 70 6d 70 74 08      00:09:58.722  READ FPDMA QUEUED
  60 08 28 48 00 00 00 08      00:09:58.722  READ FPDMA QUEUED
  60 20 20 20 00 00 00 08      00:09:58.722  READ FPDMA QUEUED

Error 58 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 01 ff 58 70 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 3f 87 c3 73 08      00:09:51.391  READ FPDMA QUEUED
  60 08 00 ff 87 c3 73 08      00:09:51.390  READ FPDMA QUEUED
  60 06 10 01 59 70 74 08      00:09:51.390  READ FPDMA QUEUED
  60 02 08 ff 58 70 74 08      00:09:51.390  READ FPDMA QUEUED
  60 07 00 38 88 c3 73 08      00:09:51.390  READ FPDMA QUEUED

Error 57 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 00 21 08 38 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 a8 00 21 08 38 02 08      00:06:57.276  WRITE FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:06:57.274  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:06:57.273  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:06:57.273  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:06:57.271  READ NATIVE MAX ADDRESS EXT

Error 56 occurred at disk power-on lifetime: 9 hours (0 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 fd 9f 01 3c e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 a8 00 9f 01 3c 02 08      00:06:50.255  WRITE FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:06:50.252  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:06:50.252  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:06:50.252  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:06:50.252  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%         9         12623379
# 2  Short offline       Completed without error       00%         3         -
# 3  Short offline       Completed without error       00%         1         -
# 4  Extended offline    Aborted by host               90%         1         -

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

---

### Post by mrsteveman1 on 2008-08-28
SMART data is sometimes hard to read and decipher, but it would appear you have 849 pending sectors. That means 849 sectors have bad data in them but can't yet be reallocated.

There is also a high number of past relocated sectors as well.

RAW number isn't always what it appears to be but sometimes it can't be anything else.

Is this a new disk?

Regardless of all of this, my first suggestion would be to save anything you want on the disk, then write zeros to the entire thing (which allows the disk to reallocate bad sectors to good ones).

---

### Post by jeremiah.bloogs99 on 2008-09-05
In the end I took the disc to a computer repair shop and asked them to test it. It failed in their machine too. I then had it replaced (with the same model) and everything now works fine. Many thanks for the help.

---

