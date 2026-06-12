---
title: "Unable to format partition"
date: 2019-09-29
forum: Installation &amp; Upgrades
---

### Post by zebrah12 on 2019-09-29
I recently used *shred* to fill my entire hard drive with random data. Afterwards I'm trying to install Ubuntu from a live USB.

However, I'm unable to create a large partition on my hard drive. I can create a */boot* partition of 6 GB, but I cannot allocate the remaining (465.76 GB) to the */home* partition. Please note that previously about 250 GB of my hard drive was formatted as NTFS, as I had Windows installed at some point.

I have pasted the error GParted is throwing below:

```
GParted 0.30.0 --enable-libparted-dmraid --enable-online-resize

 Libparted 3.2
 [TABLE]
[TR]
[TD="colspan: 2"] **Create Primary Partition #1 (ext4, 465.76 GiB) on /dev/sda**  00:00:21    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] create empty partition  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda1 (partition)
start: 2048
end: 976773119
size: 976771072 (465.76 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] clear old file system signatures in /dev/sda1  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] write 512.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 274877906944  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 512.00 KiB of zeros at byte offset 500106264576  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 500106723328  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 8.00 KiB of zeros at byte offset 500106780672  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] flush operating system cache of /dev/sda  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] set partition type on /dev/sda1  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *new partition type: ext4*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] create new ext4 file system  00:00:21    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***mkfs.ext4 -F -O ^64bit -L '' '/dev/sda1'***  00:00:21    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]64-bit filesystem support is not enabled.  The larger fields afforded  by this feature enable full-strength checksumming.  Pass -O 64bit to  rectify.
Creating filesystem with 122096384 4k blocks and 30531584 inodes
Filesystem UUID: 96c9472a-1867-4984-8e18-7f5b43c2ee33
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information:   10/3727[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]mke2fs 1.44.1 (24-Mar-2018)

Warning, had trouble writing out superblocks.
[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================


```

---

### Post by TheFu on 2019-09-29
I would create a new GPT partition table, then create any partitions, sized as you'd like, then choose the file system for each to be formatted.
Then I'd click "Apply"

If that doesn't work, I'd run some SMART tests on the disk to see if any bad sectors need to be relocated. **Smartctl** should force that. If more than 10 sectors are relocated, I'd use DBAN to wipe the disk twice and either give it away or drill 6 1/2inch holes through it.

---

### Post by zebrah12 on 2019-10-08
I ran SMART tests using **smartclt** and they did not  report any error, but I'm still getting the same error when trying to  install Ubuntu. Is there another utility I could try? Perhaps after  filling the entire hard drive with zeros some sectors got misaligned.  Could filling the drive with random data potentially fix this?

SMART test results:

```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Blue Mobile
Device Model:     WDC WD5000LPVX-75V0TT0
Serial Number:    WX21E54HMV21
LU WWN Device Id: 5 0014ee 605128008
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Tue Oct  8 10:46:49 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 8220) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  95) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       5227
  3 Spin_Up_Time            0x0027   150   145   021    Pre-fail  Always       -       1466
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5208
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   081   081   000    Old_age   Always       -       14528
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       5160
191 G-Sense_Error_Rate      0x0032   001   001   000    Old_age   Always       -       280
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       87
193 Load_Cycle_Count        0x0032   149   149   000    Old_age   Always       -       153542
194 Temperature_Celsius     0x0022   106   082   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       34
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   081   081   000    Old_age   Always       -       14034
241 Total_LBAs_Written      0x0032   200   200   000    Old_age   Always       -       31479294197
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       27567278464
254 Free_Fall_Sensor        0x0032   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               90%     14504         -
# 2  Short offline       Completed without error       00%         0         -

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

---

### Post by TheFu on 2019-10-08
```
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       **34**
```
The drive is failing.  Backup everything ASAP and move to new storage.  **You have already lost some data.**

---

