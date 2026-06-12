---
title: "Ubuntu Windows Dual Boot, boot failure"
date: 2023-06-22
forum: Installation &amp; Upgrades
---

### Post by vivek697 on 2023-06-22
Hello,
After installing recommended updates from Ubuntu software installer, I restarted my laptop and I can't seem to boot. I used a live ubuntu usb and installed boot-repair and generated the diagnostics:  [URL="https://paste.ubuntu.com/p/bF43v2wQfJ/"]https://paste.ubuntu.com/p/bF43v2wQfJ/
dsds[/URL]
I have Windows 8 installed on /dev/sda5 and Ubuntu on /dev/sda6. I use the partition /dev/sda8 for most of my files and data, available to me on both OS.

 Can someone please help ?

---

### Post by tea for one on 2023-06-22
My reply is probably not really what you want to read:-

Windows 8 reached end of life in January 2023
Back up your Windows and Ubuntu personal data
Install Windows 11 in UEFI mode with GPT 
Restore Windows data and check all is OK
Make free space for Ubuntu using Windows tools
Install Ubuntu (20.04 or 22.04) in UEFI mode

---

### Post by vivek697 on 2023-06-22
Hello,
Thanks for taking the time to reading my query and replying :)
Most of my data is backed up. I am aware that formatting everything and re-installing is an option, but as you can understand, I'd prefer to keep that as a last recourse. 

When I tried to have boot manager auto-repair, it produced an error: " GPT-detected. Please create a BIOS Boot partition then try again..." Looking up online for other posts where people have encountered this msg before, I got the suggestion to boot the live usb with UEFI mode. I did that. Here's the new log from boot-repair: [https://pastebin.ubuntu.com/p/jQ7YSJGqB5/](https://pastebin.ubuntu.com/p/jQ7YSJGqB5/) 
Two things I noted:
Boot repair does not detect the Ubuntu installation
Boot repair did not provide an option to repair

Edit: Would it be possible to atleast repair enough to recover my Ubuntu installation? I rarely use Windows so I would be okay if I was not able to boot into that. 
Thanks anyways :)

---

### Post by tea for one on 2023-06-22
> **vivek697 said:**
> Most of my data is backed up. I am aware that formatting everything and re-installing is an option, but as you can understand, I'd prefer to keep that as a last recourse.
Yes, I completely understand.
However, you have an unsupported, insecure Windows 8 system and it would be remiss of me to help you retain that system.
> Edit: Would it be possible to atleast repair enough to recover my Ubuntu installation?
Of course, it is possible but I would still suggest that you remove Windows 8 or replace it with a supported Windows 11
> I rarely use Windows so I would be okay if I was not able to boot into that. 
Therefore, install Ubuntu 22.04 in UEFI mode with GPT.
Modern, robust and future proof.

Again, I know that this is not the help you really want, but I would hope that you give my suggestion serious consideration.

---

### Post by vivek697 on 2023-06-22
I will prefer to remove windows altogether and retain my Ubuntu 20.04 installation. As I understand,  upgrading from 20.04 to 22.04 will retain my data and configurations etc.  However,  a fresh install would lose all that? 

So can you please advise how I can recover my Ubuntu 20.04
Removing windows seems easy enough-just format that partition. If not,  please advise.

---

### Post by oldfred on 2023-06-22
Your sda6 was/is your Ubuntu install?
In several places it just shows partition as unknown/unformatted. And in one as NTFS? Was it ext4 or some other format?

Does testdisk show partition. If resized multiple times, it may have several versions. You can only restore one that matches current size.
[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by yancek on 2023-06-23
I don't see how doing standard updates would create the problems you now have.  Your initial boot repair output shows Ubuntu on sda6 and the second boot repair shows nothing on sda6?  In both boot repair outputs, it shows sda2 as an EFI partition with no files for either windows or Ubuntu which would usually show.  Since there is no boot code in the MBR, that would indicate it was an EFI install and there should be boot files on that partition.  Line 86 of the first report shows Ubuntu detected while line 84 of the second report shows only windows detected so something else is going on here.  Both reports show the drive is GPT which would require an EFI boot for windows 8.  When you ran the first boot repair, it was in Legacy mode while the second was in EFI mode which could account for the differences.

You might try reinstalling Grub from the live USB in UEFI mode.  Another possible option would be to reinstall 20.04 and select to NOT format your Ubuntu partitions.

---

### Post by vivek697 on 2023-06-23
I have had a chance to read up a lot and I've tried a bunch of things. It is an interesting learning experience :)

After the first boot repair report,  among other things,  I had moved around some files on the sda6 partition, which is my Ubuntu / partition. It was an incredibly stupid thing to do as This caused a corrupt super block on that partition. 
I used:  e2fsck -b 32768 /dev/sda6 to recover. This was suggested by fsck command.   
E2fsck finds a number of errors that it tries to fix,  but ultimately terminates with "Error writing block 1 (Input/output error)."

I guess I have to fix the super block to recover the sda6 partition and then look at boot repair again with live Usb in Efi mode

I don't know how to have e2fsck move past the input/output error

---

### Post by vivek697 on 2023-06-23
I beginning to wonder if my harddisk has hardware issues, so I ran smartctl:

```
$ sudo smartctl -a /dev/sda6

smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.19.0-32-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Samsung SpinPoint M8 (AF)
Device Model:     ST1000LM024 HN-M101MBB
Serial Number:    S314JA0FA04945
LU WWN Device Id: 5 0004cf 20e4f2ae0
Firmware Version: 2BA30003
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Jun 23 13:25:17 2023 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (13440) seconds.
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
recommended polling time:      ( 224) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       8637
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   092   089   025    Pre-fail  Always       -       2446
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5612
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       25894
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       67
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5234
 13 Read_Soft_Error_Rate    0x003a   100   100   000    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       3501644
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       2202
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       246
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1022653
194 Temperature_Celsius     0x0002   061   050   000    Old_age   Always       -       39 (Min/Max 7/50)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       7
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       5
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       30368
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       24560
241 Total_LBAs_Written      0x0032   090   090   000    Old_age   Always       -       14428547
242 Total_LBAs_Read         0x0032   096   089   000    Old_age   Always       -       5500207
254 Free_Fall_Sensor        0x0032   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 7510 (device log contains only the most recent five errors)
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

Error 7510 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.352  READ DMA
  25 00 08 00 20 58 e0 00      00:00:00.352  READ DMA EXT
  25 00 08 00 d0 8d e0 00      00:00:00.352  READ DMA EXT
  27 00 00 00 00 00 e0 00      00:00:00.352  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:00:00.352  IDENTIFY DEVICE

Error 7509 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.347  READ DMA
  25 00 08 a0 65 70 e0 00      00:00:00.347  READ DMA EXT
  25 00 08 f0 17 58 e0 00      00:00:00.347  READ DMA EXT
  27 00 00 00 00 00 e0 00      00:00:00.347  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:00:00.347  IDENTIFY DEVICE

Error 7508 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.345  READ DMA
  ec 00 01 00 00 00 00 00      00:00:00.345  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      00:00:00.344  IDENTIFY DEVICE
  27 00 00 00 00 00 e0 00      00:00:00.344  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:00:00.344  IDENTIFY DEVICE

Error 7507 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.343  READ DMA
  ec 00 01 00 00 00 00 00      00:00:00.343  IDENTIFY DEVICE
  c8 00 68 88 e7 14 e0 00      00:00:00.343  READ DMA
  e5 00 00 00 00 00 00 00      00:00:00.343  CHECK POWER MODE
  c8 00 80 00 e7 14 e0 00      00:00:00.343  READ DMA

Error 7506 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.342  READ DMA
  25 00 08 20 20 58 e0 00      00:00:00.342  READ DMA EXT
  25 00 08 80 d0 8d e0 00      00:00:00.342  READ DMA EXT
  25 00 08 f8 ce 2d e0 00      00:00:00.342  READ DMA EXT
  c8 00 08 20 e8 14 e0 00      00:00:00.342  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     25889         2049
# 2  Extended offline    Completed: read failure       90%     25879         2049
# 3  Short offline       Completed: read failure       90%     25879         2049
# 4  Short offline       Completed: read failure       90%     25879         2049
# 5  Short offline       Aborted by host               80%     11638         -
# 6  Short offline       Aborted by host               90%     10816         -
# 7  Short offline       Completed without error       00%      9893         -
# 8  Short offline       Completed without error       00%      4061         -
# 9  Short offline       Aborted by host               90%      3813         -
#10  Short offline       Completed without error       00%       425         -
#11  Short offline       Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed_read_failure [90% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       8637
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   092   089   025    Pre-fail  Always       -       2446
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5612
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       25894
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       67
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5234
 13 Read_Soft_Error_Rate    0x003a   100   100   000    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       3501644
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       2202
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       246
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       1022653
194 Temperature_Celsius     0x0002   060   050   000    Old_age   Always       -       40 (Min/Max 7/50)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       7
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       5
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       30368
240 Head_Flying_Hours       0x0032   100   100   000    Old_age   Always       -       24560
241 Total_LBAs_Written      0x0032   090   090   000    Old_age   Always       -       14428547
242 Total_LBAs_Read         0x0032   096   089   000    Old_age   Always       -       5500207
254 Free_Fall_Sensor        0x0032   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 7510 (device log contains only the most recent five errors)
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

Error 7510 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.352  READ DMA
  25 00 08 00 20 58 e0 00      00:00:00.352  READ DMA EXT
  25 00 08 00 d0 8d e0 00      00:00:00.352  READ DMA EXT
  27 00 00 00 00 00 e0 00      00:00:00.352  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:00:00.352  IDENTIFY DEVICE

Error 7509 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.347  READ DMA
  25 00 08 a0 65 70 e0 00      00:00:00.347  READ DMA EXT
  25 00 08 f0 17 58 e0 00      00:00:00.347  READ DMA EXT
  27 00 00 00 00 00 e0 00      00:00:00.347  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:00:00.347  IDENTIFY DEVICE

Error 7508 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.345  READ DMA
  ec 00 01 00 00 00 00 00      00:00:00.345  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      00:00:00.344  IDENTIFY DEVICE
  27 00 00 00 00 00 e0 00      00:00:00.344  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:00:00.344  IDENTIFY DEVICE

Error 7507 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.343  READ DMA
  ec 00 01 00 00 00 00 00      00:00:00.343  IDENTIFY DEVICE
  c8 00 68 88 e7 14 e0 00      00:00:00.343  READ DMA
  e5 00 00 00 00 00 00 00      00:00:00.343  CHECK POWER MODE
  c8 00 80 00 e7 14 e0 00      00:00:00.343  READ DMA

Error 7506 occurred at disk power-on lifetime: 25893 hours (1078 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 01 08 00 e0  Error: UNC 7 sectors at LBA = 0x00000801 = 2049

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 08 00 e0 00      00:00:00.342  READ DMA
  25 00 08 20 20 58 e0 00      00:00:00.342  READ DMA EXT
  25 00 08 80 d0 8d e0 00      00:00:00.342  READ DMA EXT
  25 00 08 f8 ce 2d e0 00      00:00:00.342  READ DMA EXT
  c8 00 08 20 e8 14 e0 00      00:00:00.342  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     25889         2049
# 2  Extended offline    Completed: read failure       90%     25879         2049
# 3  Short offline       Completed: read failure       90%     25879         2049
# 4  Short offline       Completed: read failure       90%     25879         2049
# 5  Short offline       Aborted by host               80%     11638         -
# 6  Short offline       Aborted by host               90%     10816         -
# 7  Short offline       Completed without error       00%      9893         -
# 8  Short offline       Completed without error       00%      4061         -
# 9  Short offline       Aborted by host               90%      3813         -
#10  Short offline       Completed without error       00%       425         -
#11  Short offline       Completed without error       00%         0         -

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed_read_failure [90% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by vivek697 on 2023-06-23
I don't really know how to interpret all of this, but it begins with overall health assessment passed, so I'm guessing the disk is fine? What do I do then for e2fsck unable to write block 1 (input.output error).

---

### Post by oldfred on 2023-06-23
Please use Code Tags.
Easy to add in Forum's Advanced Editor with # icon.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

