---
title: "Ubuntu doesn't boot with new Kernel"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by marco135 on 2016-05-13
Hi guys,

I'm new to this forum and quite new to Ubuntu, so you can call me a noob. I have UBUNTU KXSTUDIO Studio (Ubuntu 14.04.4 LTS) running on a new PC since January this year. There was a kernel update 3 days ago and after this update i'm not able to boot with the kernel 3.13.0-86-lowlatency. However with kernel version 3.13.0-85-lowlatency it works after I entered grub. The message I get is:

```

 &#8212; Boot args (cat /proc/cmdline)

&#8212; Check rootdelay= (did the system wait long enough?)

&#8212; Check root= (did the system wait for the right device?)

&#8212; Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/kxstudio--vg-root does not exist. Dropping to a shell! 
BusyBox v.1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash) 
Enter 'help' for list of built-in commands .

(initramfs)..

```

I also checked the SSD (Samsung EVO 850) and I think it looks fine (?)
```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-85-lowlatency] (local build) Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Samsung based SSDs
Device Model:     Samsung SSD 850 EVO 250GB
Serial Number:    S21PNXDG907533P
LU WWN Device Id: 5 002538 d405c9bac
Firmware Version: EMT01B6Q
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu May 12 21:05:02 2016 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x53) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 133) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       117
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       79
177 Wear_Leveling_Count     0x0013   099   099   000    Pre-fail  Always       -       1
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   069   059   000    Old_age   Always       -       31
195 ECC_Error_Rate          0x001a   200   200   000    Old_age   Always       -       0
199 CRC_Error_Count         0x003e   100   100   000    Old_age   Always       -       0
235 POR_Recovery_Count      0x0012   099   099   000    Old_age   Always       -       2
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       597710729

SMART Error Log Version: 1
No Errors Logged

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       117         -
# 2  Short offline       Aborted by host               80%       117         -
# 3  Extended offline    Completed without error       00%       117         -
# 4  Extended offline    Completed without error       00%       116         -
# 5  Short offline       Completed without error       00%       116         -
# 6  Extended offline    Completed without error       00%       116         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
  255        0    65535  Read_scanning was never started
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

I asked already in another forum but didn't get any advice that's why I try it here. 
Any advice is highly appreciated :)

---

### Post by lukeiamyourfather on 2016-05-13
If booting from the old kernel still works then the SSD is unlikely the issue. Did you install any drivers from source like proprietary graphics drivers or RAID controller drivers?

---

### Post by marco135 on 2016-05-13
> **lukeiamyourfather said:**
> If booting from the old kernel still works then the SSD is unlikely the issue. Did you install any drivers from source like proprietary graphics drivers or RAID controller drivers?

Thank's for your replay. No I didn't install anything. :/ Except of the automatic updates via muon.

---

### Post by marco135 on 2016-05-13
I've seen that last sunday some packages were removed by muon that were not needed. Thereunder lvm2. What I find a bit strange now is:

```
fox@fox-MS-7817:~$ sudo blkid 
[sudo] password for fox:
/dev/sda1: UUID="ffb6d95f-fa8d-4ce7-8b13-0f378b9975e7" TYPE="ext2" 
/dev/sda5: UUID="JBEjVc-UDkO-69O0-qoLX-knpf-bryX-oFY8ua" TYPE="LVM2_member" 
/dev/mapper/kxstudio--vg-root: UUID="905d47ec-94e1-40f1-aa07-e96e1b24e05e" TYPE="ext4" 
/dev/mapper/kxstudio--vg-swap_1: UUID="f0c48bfc-b39f-43e6-8f75-d3849714e88a" TYPE="swap" 
fox@fox-MS-7817:~$ 

```

```
ox@fox-MS-7817:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 Köpfe, 63 Sektoren/Spur, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x000a108f

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Erweiterte
/dev/sda5          501760   488396799   243947520   8e  Linux LVM

Disk /dev/mapper/kxstudio--vg-root: 241.8 GB, 241810014208 bytes
255 Köpfe, 63 Sektoren/Spur, 29398 Zylinder, zusammen 472285184 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x00000000

Festplatte /dev/mapper/kxstudio--vg-root enthält keine gültige Partitionstabelle

Platte /dev/mapper/kxstudio--vg-swap_1: 7985 MByte, 7985954816 Byte
255 Köpfe, 63 Sektoren/Spur, 970 Zylinder, zusammen 15597568 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x00000000

Festplatte /dev/mapper/kxstudio--vg-swap_1 enthält keine gültige Partitionstabelle
fox@fox-MS-7817:~$ 

```

---

