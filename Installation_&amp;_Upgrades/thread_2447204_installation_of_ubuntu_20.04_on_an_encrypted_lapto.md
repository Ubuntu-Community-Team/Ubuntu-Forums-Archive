---
title: "installation of ubuntu 20.04 on an encrypted laptop"
date: 2020-07-14
forum: Installation &amp; Upgrades
---

### Post by paola812 on 2020-07-14
Dear all,

    my laptop is(was??) encrypted (I've the password). I wanted to install ubuntu 20.04 on it from a usb drive. During the installation process I get an error saying something like "input/output error : I cannot write on dev/sda". The installation process never goes beyond "Choose your country"

I've used testdisk to check the disk and the short version ends without any error ("tests passed"), while the long version never reaches the end (10% remains after several hours).
I have tried the command :
```
sudo badblocks -nvs /dev/sda
```
and got, after few seconds : 
Input/output error during test data write, block 1280 (and many other block numbers)
The output looked like (0/0/XXX <- a high number)
I have tried :
```
sudo hdparm --read-sector 1280 /dev/sda

/dev/sda:
reading sector 1280: succeeded
0120 1b07 109c 0401 9058 0100 0710 a804
0190 5801 0007 10c4 0402 e264 0300 0710
cc04 02e0 6403 0007 10d4 0402 201d 0200
0710 580f 02dc 8103 0007 1064 0f02 0483
0300 0710 6c0f 0200 1d02 0007 1074 0f02
ec81 0300 0710 7c0f 02fc 8103 0007 1088
0f02 1083 0300 0710 900f 0200 1d02 0007
1098 0f02 0c82 0300 0710 a40f 021c 8303
0007 10ac 0f02 001d 0200 0710 b40f 021c
8203 0007 10c0 0f02 2883 0300 0710 c80f
0200 1d02 0007 10d0 0f02 2c82 0300 0710
dc0f 023c 8203 0007 10e8 0f02 4c82 0300
0700 f80f 0132 5e07 105c 0d02 001d 0200
0710 600d 01e5 9701 0007 106c 0d02 001d
0200 0710 700d 01e5 9701 0007 107c 0d01
e597 0100 0710 880d 01e5 9701 0007 1094
0d01 261b 0200 0710 a40d 0274 8203 0007
10ac 0d02 001d 0200 0710 b40d 024c 8003
0007 10bc 0d02 5c80 0300 0710 c40d 026c
8003 0007 10cc 0d02 7c80 0300 0710 d80d
0280 8203 0007 10e0 0d02 001d 0200 0710
e80d 028c 8003 0007 10f0 0d02 9c80 0300
0710 fc0d 028c 8203 0007 1004 0e02 001d
0200 0710 0c0e 02ac 8003 0007 1014 0e02
bc80 0300 0710 200e 0298 8203 0007 1028
0e02 001d 0200 0710 300e 02cc 8003 0007
1038 0e02 dc80 0300 0710 440e 02a4 8203
0007 104c 0e02 001d 0200 0710 540e 02ec
8003 0007 105c 0e02 fc80 0300 0710 680e
02b0 8203 0007 1070 0e02 001d 0200 0710
780e 020c 8103 0007 1080 0e02 1c81 0300
0710 8c0e 02bc 8203 0007 1094 0e02 001d
```

and repeating the command it gives always the same output.
I then tried to write on it with :
```
sudo hdparm --write-sector  1280 --yes-i-know-what-i-am-doing /dev/sda

/dev/sda:
re-writing sector 1280: SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 04 51 00 01 21 04 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
succeeded

```
But we lunching again 
```
sudo hdparm --read-sector 1280 /dev/sda
```
the output is the same and also 
```
sudo badblocks -nvs /dev/sda
```
gives the same output as before for the block 1280

Can someone give me a hint please to go up to the end of the ubuntu installation despite this issue?

Thank you very much
Cheers

Paola

PS Please, an easy answer : I'm a newbie :)

---

### Post by TheFu on 2020-07-14
There isn't any easy answer sorry

Use smartctl to see what the drive knows about it's own failures
if there are any "pending sectors for relocation" buy a new HDD
Also check the number of already relocated sectors  if that number is non-zero the drive is starting to fail  it that number is over 10 i'd replace the HDD

Whenever using encryption excellent backups are required since recovery tools don't work

I&#8217;m confused by the jump from can't install lead to running bad blocks?  That's a new jump for me

---

### Post by paola812 on 2020-07-18
Dear TheFu,

    thank you for your reply.

The disk looks good at all the tests I did, still it really seems it cannot write on most of the disk (while it can read it). Smartctl also doesn't give any error, neither the short not the long version, although it doesn't come up to the end of the long test, saying 10% is left. No pending sectors for relocation and not already relocated sectors, as far as I could see.

We got from "I cannot install" to running bad block as the error I got while trying to install was something like "I cannot write on dev/sda" during the installation. I could not understand why, so I thought something was wrong/broken in the disk. I tried smartctl and then bad blocks to see if the remaining 10% which could not be analysed was due to some error.

So, if I understand your answer, there is no way to install ubuntu (or anything else) on an encrypted laptop, is it right? (I don't need to recover the data, I've a backup, i just need to install an operating system on it)

Thank you very much TheFu
Cheers
Paola

---

### Post by TheFu on 2020-07-18
Usually, we like to see facts (commands and command output), not descriptions here. It prevent misunderstandings on both sides.  Assuming the SMART data is truly fine, as claimed, then, a disk that goes into read-only mode is doing that because the OS thinks it isn't safe to be in write mode.  

Was the any other data on the disk before?  If it was connected to Windows, it is possible that Windows didn't close the file system(s) properly so Linux won't touch them.  Also, the disk or partitions could be marked as used by RAID. If that's true, you'll need to clear those "RAID bits" before using the disk.  I always have to look up how to do that, but since you are comfortable reading SMART output, I'll assume you can search and solve that, if needed.

If you are positive that nothing on the disk is needed, use that install disk, boot into "Try Ubuntu" mode and use gparted to delete all the partitions and lay down a new GPT partition table.  Then you can choose to install using the desktop icon "Install Ubuntu" .... and choose to use encryption+LVM.

My point about file recovery tools not working was for after the OS + encryption is installed.  Once that happens, if there is any physical corruption, only backup data will be useful. No data recovery tools will work on a properly encrypted data store - and dmcrypt+LUKS is most definitely properly encrypted.

Would be helpful to know if the target storage is a HDD or an SSD.  A sign of a failing SSD is that the drive goes into read-only mode.

---

### Post by paola812 on 2020-07-21
Dear TheFu,

   sorry for not providing the smartctl output before. You are right : as I'm a newbie it's ways better than someone more expert than me reads the output of the commands Here it is :

```
sudo smartctl -t short /dev/sda
```
```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-26-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Tue Jul 21 20:49:07 2020 UTC
```

```
sudo smartctl -l selftest /dev/sda
``` gives
```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-26-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     15780         -
# 2  Extended offline    Completed without error       00%     15779         -
# 3  Short offline       Completed without error       00%     15779         -
# 4  Extended offline    Aborted by host               10%     15704         -
# 5  Short offline       Completed without error       00%     15704         -
# 6  Extended offline    Aborted by host               10%     15704         -
# 7  Extended offline    Aborted by host               20%     15696         -
# 8  Short offline       Completed without error       00%     15695         -
# 9  Short offline       Completed without error       00%     15695         -
#10  Short offline       Completed without error       00%     10014         -
#11  Short offline       Completed without error       00%     10014         -
#12  Short offline       Completed without error       00%      3204         -
#13  Short offline       Completed without error       00%         3         -

```
The command :
```
sudo smartctl -t long /dev/sda
```
gives 
[/CODE]smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-26-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Samsung based SSDs
Device Model:     SAMSUNG SSD PM830 FDE mSATA 256GB
Serial Number:    S0ZWNYAD502424
LU WWN Device Id: 5 002538 043584d30
Firmware Version: CXM83D1Q
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Wed Jul 22 05:54:33 2020 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x83)    Offline data collection activity
                    is in a Reserved state.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 1020) seconds.
Offline data collection
capabilities:              (0x53) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      (  17) minutes.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       15787
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       4412
175 Program_Fail_Count_Chip 0x0032   100   100   010    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   100   100   010    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0013   090   090   010    Pre-fail  Always       -       335
178 Used_Rsvd_Blk_Cnt_Chip  0x0013   095   095   010    Pre-fail  Always       -       156
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   095   095   010    Pre-fail  Always       -       304
180 Unused_Rsvd_Blk_Cnt_Tot 0x0013   095   095   010    Pre-fail  Always       -       6224
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
195 ECC_Error_Rate          0x001a   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 CRC_Error_Count         0x003e   253   253   000    Old_age   Always       -       0
232 Available_Reservd_Space 0x0013   095   095   000    Pre-fail  Always       -       3108
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       29069747454
242 Total_LBAs_Read         0x0032   099   099   000    Old_age   Always       -       64077724089

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     15781         -
# 2  Short offline       Completed without error       00%     15780         -
# 3  Short offline       Completed without error       00%     15780         -
# 4  Extended offline    Completed without error       00%     15779         -
# 5  Short offline       Completed without error       00%     15779         -
# 6  Extended offline    Aborted by host               10%     15704         -
# 7  Short offline       Completed without error       00%     15704         -
# 8  Extended offline    Aborted by host               10%     15704         -
# 9  Extended offline    Aborted by host               20%     15696         -
#10  Short offline       Completed without error       00%     15695         -
#11  Short offline       Completed without error       00%     15695         -
#12  Short offline       Completed without error       00%     10014         -
#13  Short offline       Completed without error       00%     10014         -
#14  Short offline       Completed without error       00%      3204         -
#15  Short offline       Completed without error       00%         3         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.[/CODE]



To answer to your other questions : 
a. > Would be helpful to know if the target storage is a HDD or an SSD.  A  sign of a failing SSD is that the drive goes into read-only mode.         
It's the internal hard disk of the laptop

b.> Was the any other data on the disk before?  If it was connected to  Windows, it is possible that Windows didn't close the file system(s)  properly so Linux won't touch them.  Also, the disk or partitions could  be marked as used by RAID. If that's true, you'll need to clear those  "RAID bits" before using the disk.  I always have to look up how to do  that, but since you are comfortable reading SMART output, I'll assume  you can search and solve that, if needed.
Yes, windows was installed on it before and it was encripted with BitLocker. Ok I'll try to find the procedure to clear "RAID bits" (I admit that I've no clue on what it means though)
For information, 
```
sudo fdisk -l 
```
gives : 
```
Disk /dev/loop0: 1.93 GiB, 2049204224 bytes, 4002352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 27.9 MiB, 28405760 bytes, 55480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 240.82 MiB, 252493824 bytes, 493152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk model: SAMSUNG SSD PM83
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x95b48279

Device     Boot Start    End Sectors  Size Id Type
/dev/sda1  *       63 144584  144522 70.6M ef EFI (FAT-12/16/32)

Disk /dev/sdb: 7.38 GiB, 7918845952 bytes, 15466496 sectors
Disk model: GOODRAM 8GB     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00039877

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15466495 15464448  7.4G  c W95 FAT32 (LBA)

```
(where /dev/sdb is the bootable usb key that I'm using to boot on ubuntu). It doesn't seem to me that "RAID" appears anywhere, but I'm not sure on how it should appear in this list.
Anyway, I run the following command
  ```
sudo dmraid -r -E /dev/sda
```
which gives : 
```
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
... a lot of "ERROR: pdc: reading /dev/sda[Input/output error]" which I remove not to make this post too long
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
no raid disks and with names: "/dev/sda"

```

I guess it means that there is no RAID, does it?


c. > If you are positive that nothing on the disk is needed, use that install  disk, boot into "Try Ubuntu" mode and use gparted to delete all the  partitions and lay down a new GPT partition table.  Then you can choose  to install using the desktop icon "Install Ubuntu" .... and choose to  use encryption+LVM.
This is what I started with and I don't manage to go up to the end. Gparted (as well as the partition tool that I can select from the Ubuntu installation procedure) tells me : 
```
/dev/sda1   fat32 WAVE   70.57 MiB(size)  9.04MiB(used)  61.52MiB(unused) boot,eps (flags)
unallocated                       238.41GiB

```  

I then try to create a new partition (click right -> New) in the unallocated part. 512MiB as Primary Partition, filesystem : linux-swap; label : swap
and I get the following message
```
Input/output error during write on /dev/sda
```

Searching online, I also tried ```
mkusb
```
with the option "d" and here is the output (I was expecting gparted to be allowed to write on the disk after this, but I still get the same input/output error message)
```
[FONT=Calibri][SIZE=3][COLOR=black][FONT=Calibri][SIZE=2][FONT=arial]---------------------------------------------------------------------
 Usage: mkusb [input-file]      # optional parameter
 ---------------------------------------------------------------------
 d:  dus , guidus, mkusb-dus    - Classic, easy to use
 p: Plug,   mkusb-plug          - New, easy to use
 n: NoX,    sudo mkusb-nox      - original text mode
 b: Bas,    sudo mkusb-bas      - basic text mode for old/basic linux
 e: Eleven, sudo -H mkusb-11    - Old user interface
 q: Quit
 ---------------------------------------------------------------------
 Select version of mkusb (d/p/n/b/e/q) d
  dus 12.5.7 
 live system or temporary superuser permissions
 wipe the whole device - it can take very long time
 Live drive, that is booted from: /dev/sdb
 cands=1
 sda
 SAMSUNG_SSD_PM830_FDE_mSATA_256GB
 238.5G
 ata
 built-in device
 p_target: target=/dev/sda
 target drive size = 256 GB
 Preparing to wipe  /dev/sda 
 MODEL                             NAME   FSTYPE LABEL   SIZE
 SAMSUNG_SSD_PM830_FDE_mSATA_256GB sda                 238.5G
                                   &#9492;&#9472;sda1               70.6M
 wipe-whole-device
 /dev/sda
 -----
 live system or temporary superuser permissions
 Trying to unmount partitions if mounted on the target device
 umount: /dev/sda: not mounted.
 umount: /dev/sda1: not mounted.
 -------------------------------------------------------------------------------
  wipe-whole-device 
  238GiB 68:00:58 [1021KiB/s]  [=====================================================================================>]  100%            
 Syncing the device ...
 dd: error writing '/dev/sda': No space left on device
 62514775+0 records in
 62514774+0 records out
 256060514304 bytes (256 GB, 238 GiB) copied, 244859 s, 1.0 MB/s
  Done, but you should also check for the line 
 'dd: error writing to '/dev/sda': No space left on device',
 which means that the whole device is wiped. (Look a few lines above ^) 
 Wait 5 seconds and a little more ...
 Model: ATA SAMSUNG SSD PM83 (scsi)
 Disk /dev/sda: 256GB
 Sector size (logical/physical): 512B/512B
 Partition Table: msdos
 Disk Flags: 
 
 Number  Start   End     Size    Type     File system  Flags
  1      32.3kB  74.0MB  74.0MB  primary  fat32        boot, esp
 
  
 MODEL                             NAME   FSTYPE LABEL
 SAMSUNG_SSD_PM830_FDE_mSATA_256GB sda           
                                   &#9492;&#9472;sda1        
 p_clean:
 live system or temporary superuser permissions
 clean if necessary and return
 clean if necessary and quit


[COLOR=black][COLOR=black]Check the result (scroll if possible), press Enter to finish
 
 The target device is unmounted and you can unplug it.
 The system might not see the current partition table of the
 target device unless you re-plug it.

[/COLOR][/COLOR][/FONT][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```

While ```
dmesg | less  
``` while lunching gparted gives : 
```
[ 4321.952516] ata1.00: status: { DRDY ERR }
[ 4321.952517] ata1.00: error: { ABRT }
[ 4321.969831] ata1.00: supports DRM functions and may not be fully accessible
[ 4321.987201] ata1.00: ATA Identify Device Log not supported
[ 4321.987206] ata1.00: Security Log not supported
[ 4322.014575] ata1.00: supports DRM functions and may not be fully accessible
[ 4322.031915] ata1.00: ATA Identify Device Log not supported
[ 4322.031920] ata1.00: Security Log not supported
[ 4322.031934] ata1.00: configured for UDMA/33
[ 4322.031962] ata1: EH complete
[ 4322.068582] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 4322.068592] ata1.00: irq_stat 0x40000001
[ 4322.068598] ata1.00: failed command: READ DMA EXT
[ 4322.068610] ata1.00: cmd 25/00:08:f8:2e:cf/00:00:1d:00:00/e0 tag 0 dma 4096 in
                        res 51/04:08:f8:2e:cf/00:00:1d:00:00/00 Emask 0x1 (device error)

```

And ```
ubuntu@ubuntu:~$ sudo fsck /dev/sda

fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/sda

```

d. > My point about file recovery tools not working was for after the OS +  encryption is installed.  Once that happens, if there is any physical  corruption, only backup data will be useful. No data recovery tools will  work on a properly encrypted data store - and dmcrypt+LUKS is most  definitely properly encrypted.
OK, got it, thank you! For the moment I would be very happy to be able to install ubuntu without any encryption :(

Thank you very much for your help, I really appreciate it

Paola

---

### Post by TheFu on 2020-07-21
Haven't read the entire reply, but 
> sudo smartctl -a /dev/sda
is the command to see the test results from smart. The other commands simply request different types of tests.

> a. It's the internal hard disk of the laptop
That doesn't answer the question. Is it an SSD or spinning rust?
**/dev/sda: 238.49 GiB** being a Samsung SSD seems likely.  That device was first made in 2011, so it has had a very long life already.  Dying now isn't unexpected.

BTW, all output for "loop" devices is useless. No need to ever include that unless the issue is specifically about loop mounting.  If you can edit the post and remove that, it will encourage others to look, since they wouldn't need to filter through all the loop crap.

If you never used RAID, then it is highly unlike the RAID bits were ever set.  OTOH, I don't know anything about bitlocker.

At this point, the smart data is still needed.

This command, **sudo fsck /dev/sda** is incorrect. fsck isn't run against a whole hard disk, it is run against whatever device has a file system - a supported file system. Using fsck on Windows file systems doesn't work.  80% of the time, a file system would be on a partition, not the entire disk. The other 19.99999% the file system would be on some sort of logical volume - like when ZFS, btrfs or LVM are used. Using those isn't accidental. It is a proactive choice.

I think the SSD is dead.  That never happens when it is convenient, but at least you are between OSes.  OTOH, SSDs are pretty cheap and easy to swap with just a few screws even on a laptop.  Hopefully, the smart data will confirm that, but it may not. About 22% of the time, storage fails without any SMART data aberrations.

---

