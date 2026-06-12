---
title: "Error while creating ext4 file system"
date: 2019-09-30
forum: Installation &amp; Upgrades
---

### Post by en3rg1zer on 2019-09-30
Hi!

I'm trying to install ubuntu on a laptop with an SSD, but every time the installer reports that it failed to create the ext4 file system. I've booted into ubuntu live and runned gparted to try to figure out what was going on. As expected, when asked to create a ext4 partition on the SSD, gparted reports that it can't create the ext4 file system (i've tried with gpt and msdos partition tables). Here is gparted report:

GParted 0.30.0 --enable-libparted-dmraid --enable-online-resize
 Libparted 3.2
  [TABLE]
[TR]
[TD="colspan: 2"] **Create Primary Partition #1 (ext4, 223.57 GiB) on /dev/sda**  00:01:40    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] create empty partition  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda1 (partition)
start: 2048
end: 468860927
size: 468858880 (223.57 GiB)[/I][/TD]
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
[TD="colspan: 2"] write 512.00 KiB of zeros at byte offset 240055222272  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 4.00 KiB of zeros at byte offset 240055681024  00:00:00    ( SUCCESS )[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] write 8.00 KiB of zeros at byte offset 240055738368  00:00:00    ( SUCCESS )[/TD]
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
[TD="colspan: 2"] create new ext4 file system  00:01:39    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] ***mkfs.ext4 -F -O ^64bit -L '' '/dev/sda1'***  00:01:39    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]64-bit filesystem support is not enabled.  The larger fields afforded  by this feature enable full-strength checksumming.  Pass -O 64bit to  rectify.
Discarding device blocks: done                            
Creating filesystem with 58607360 4k blocks and 14655488 inodes
Filesystem UUID: 7185c7e3-1254-4567-8c0e-76ee30904780
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information:          [/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]mke2fs 1.44.1 (24-Mar-2018)

Warning, had trouble writing out superblocks.
[/I][I]
========================================[/I]
[/TD]
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

Does anyone have any idea of what might be the problem? It's driving me crazy not to understand what the hell is going on...

Thanks in advance!

---

### Post by SeijiSensei on 2019-09-30
How about not using the 64-bit option?  I've never had a problem with
```
sudo mkfs -t ext4 /dev/XXX
```

Have you tried checking for badblocks with

```
sudo mkfs -c -t ext4 /dev/sda1
```

You'll need to run this overnight as the block-level checking takes quite a while.

---

### Post by en3rg1zer on 2019-09-30
Here's what I got

[INDENT]ubuntu@ubuntu:~$ sudo mkfs -t ext4 /dev/sda1
mke2fs 1.44.1 (24-Mar-2018)
/dev/sda1 contains a vfat file system
Proceed anyway? (y,N) y
Discarding device blocks: done                            
Creating filesystem with 58607360 4k blocks and 14655488 inodes
Filesystem UUID: 31fe3511-9f74-4edc-b2bc-ab77648fd0c1
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information:          
Warning, had trouble writing out superblocks.
[/INDENT]
 
So I guess no luck...
I'm currently checking for badblocks. I'll post the results when it finishes.

Thank you!

---

### Post by en3rg1zer on 2019-09-30
So... the command
```

sudo mkfs -c -t ext4 /dev/sda1

```
didn't find any badblocks... any more ideas? :/
Do you think it can be a hardware problem? Or have anything to do with the BIOS?

---

### Post by ubfan1 on 2019-09-30
Does the comand sudo smartctl -a /dev/sda (from the smartmontools package) show any errors?

---

### Post by en3rg1zer on 2019-10-01
Here is the output from smartctl

```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.18.0-15-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA-TR200
Serial Number:    38PB62AOK3LS
LU WWN Device Id: 5 00080d c00bdca61
Firmware Version: SBFA12.4
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   Unknown(0x0ff8) (minor revision not indicated)
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Oct  1 12:44:59 2019 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection:         (   30) seconds.
Offline data collection
capabilities:              (0x00)     Offline data collection not supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       94
 12 Power_Cycle_Count       0x0012   100   100   000    Old_age   Always       -       156
167 Unknown_Attribute       0x0022   100   100   000    Old_age   Always       -       0
168 Unknown_Attribute       0x0012   100   100   000    Old_age   Always       -       0
169 Unknown_Attribute       0x0003   100   100   010    Pre-fail  Always       -       0
173 Unknown_Attribute       0x0012   198   198   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0012   100   100   000    Old_age   Always       -       45
194 Temperature_Celsius     0x0023   073   063   020    Pre-fail  Always       -       27 (Min/Max 15/37)
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       25898

SMART Error Log Version: 1
ATA Error Count: 1
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

Error 1 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 38 00 08 64 e0  Error: ICRC, ABRT at LBA = 0x00640800 = 6555648

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 38 00 08 64 e0 08      00:00:00.000  WRITE DMA
  ca 00 08 00 08 40 e0 08      00:00:00.000  WRITE DMA
  ca 00 38 00 08 24 e0 08      00:00:00.000  WRITE DMA
  ca 00 38 00 08 1c e0 08      00:00:00.000  WRITE DMA
  ca 00 38 00 08 14 e0 08      00:00:00.000  WRITE DMA

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Selective Self-tests/Logging not supported

```

I'm not sure how to interpret the results...

---

### Post by ubfan1 on 2019-10-01
Nothing looks bad, but since the device is not in the smart database, the "unknown attribute"s may be things of interest like  "Retired_Block_Count", or "Wear_Range_Delta" so watch for increases from 0.

---

### Post by en3rg1zer on 2019-10-01
So another deadend... Seriously, this thing is driving me crazy...

---

### Post by TheFu on 2019-10-01
> No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Did you run any smartctl tests first?  The -a option shows the results from tests. 

BTW, showing **sudo parted -lm** would be helpful. As would **lsblk -o name,size,type,fstype,mountpoint**

I suspect it is either a disk/storage issue or a controller issue or a cable issue.  Change the port used, change the cable used.

---

### Post by rbmorse on 2019-10-01
I saw this error the other day working with an SSD in an external case with NVMe/USB converter connected via a USB port.  Too many variables there to try and figure out what was going on.  However, on a hunch I used gparted to create a new partition table on the device and it began working as it should.  YMMV.

---

### Post by en3rg1zer on 2019-10-01
> **TheFu said:**
> Did you run any smartctl tests first?  The -a option shows the results from tests.

Sorry, I didn't. I tried it now, but when I run a test it says that self-test functions are not supported:

```

ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.18.0-15-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Self-test functions not supported

Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Command "Execute SMART Extended self-test routine immediately in off-line mode" failed: scsi error badly formed scsi parameters

```

> **TheFu said:**
> I suspect it is either a disk/storage issue or a controller issue or a cable issue.  Change the port used, change the cable used.

I can't... it's a laptop... :/

> **TheFu said:**
> BTW, showing **sudo parted -lm** would be helpful. As would **lsblk -o name,size,type,fstype,mountpoint**

Here are the results for **sudo parted -lm **(the Kingston DataTraveler is the USB pen from where I'm live booting):
```

ubuntu@ubuntu:~$ sudo parted -lm
BYT;
/dev/sda:240GB:scsi:512:512:msdos:ATA TOSHIBA-TR200:;
1:1049kB:240GB:240GB:::;

BYT;
/dev/sdb:7736MB:scsi:512:512:msdos:Kingston DataTraveler 3.0:;
1:1049kB:7736MB:7735MB:fat32::boot, lba;

```

and **lsblk -o name,size,type,fstype,mountpoint**:
```

ubuntu@ubuntu:~$ sudo lsblk -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE FSTYPE   MOUNTPOINT
loop0    1.8G loop squashfs /rofs
loop1     91M loop squashfs /snap/core/6350
loop2   34.6M loop squashfs /snap/gtk-common-themes/818
loop3  140.7M loop squashfs /snap/gnome-3-26-1604/74
loop4    2.3M loop squashfs /snap/gnome-calculator/260
loop5     13M loop squashfs /snap/gnome-characters/139
loop6   14.5M loop squashfs /snap/gnome-logs/45
loop7    3.7M loop squashfs /snap/gnome-system-monitor/57
sda    223.6G disk          
&#9492;&#9472;sda1 223.6G part          
sdb      7.2G disk          
&#9492;&#9472;sdb1   7.2G part vfat     /cdrom

```

---

### Post by en3rg1zer on 2019-10-01
> **rbmorse said:**
> I saw this error the other day working with an SSD in an external case with NVMe/USB converter connected via a USB port.  Too many variables there to try and figure out what was going on.  However, on a hunch I used gparted to create a new partition table on the device and it began working as it should.  YMMV.

Well, this SSD is connected through SATA (it's the internal storage device of the laptop). I have already created a new partition table on the device and the problem subsists...

Btw, it might be worth mentioning that I replaced the SSD a couple of months back (it had a HDD) and it has been running windows...

---

### Post by TheFu on 2019-10-01
Thanks.

SMART has to be enabled in the BIOS.  Check that. It has been a long time since I came across a BIOS that didn't have SMART already enabled.  Any storage device made in the last 25 yrs or so will support SMART unless there is some really cheap USB connection.  Yours appears to be a normal SATA SSD 2.5inch in size.  You can swap that out if this doesn't get solved, fairly cheap.  I have a Samsung 860 SSD SATA/2.5in in my laptop. It does everything fine.  I'd try to use a cheap 2.5in SATA spinning disk I have laying around first, just to validate that it isn't an issue with the motherboard or disk controller or cable first. If you don't have one, perhaps you can borrow one from a friend?

Run the SMART tests, then run the report.

Might need to re-seat the SSD as the only want to check the cable.

Besides using **gparted**, have you tried to use either **fdisk** or **parted**?  I prefer to use gparted too, but if it isn't working, moving to the other tools isn't really THAT hard.  I suspect none will work, but won't know until you try.  In fdisk and parted, the partition type would be "Linux", not ext4.  Then you'd use mkfs -t ext4 to create the file system.  If it were me and I didn't want to use LVM, I'd make 3 partitions.
/ - 25G ext4 for the OS and applications
swap 4.1G - the only size I use for laptops/desktops (non-servers). use the **mkswap** command.
/home - 50G or so. I'd leave the rest of the disk unused, for now.

While I was at it, I'd use a GPT, not MSDOS/MBR partition table.  If I wanted to use LVM, I'd do things very differently.

But as for doing the installation, there usually isn't any need to pre-partition. Do that inside the installer, to it will handle legacy or UEFI setup for you. I see that isn't working for you and it is the reason you are here.  The installer doesn't use fdisk or parted or gparted to do partitioning, so it is likely some sort of hardware issue.

---

### Post by en3rg1zer on 2019-10-01
> **TheFu said:**
> SMART has to be enabled in the BIOS.  Check that. It has been a long time since I came across a BIOS that didn't have SMART already enabled.  Any storage device made in the last 25 yrs or so will support SMART unless there is some really cheap USB connection.  Yours appears to be a normal SATA SSD 2.5inch in size.  You can swap that out if this doesn't get solved, fairly cheap.  I have a Samsung 860 SSD SATA/2.5in in my laptop. It does everything fine.  I'd try to use a cheap 2.5in SATA spinning disk I have laying around first, just to validate that it isn't an issue with the motherboard or disk controller or cable first. If you don't have one, perhaps you can borrow one from a friend?

Run the SMART tests, then run the report.

There is no option related to SMART on the BIOS... in fact, this BIOS is pretty poor. It doesn't even have a list with the available storage devices (except for the boot order list...). Is there any other way of enabling SMART?

> **TheFu said:**
> Might need to re-seat the SSD as the only want to check the cable.

That was one of the first things I did... :/

> **TheFu said:**
> Besides using **gparted**, have you tried to use either **fdisk** or **parted**?  I prefer to use gparted too, but if it isn't working, moving to the other tools isn't really THAT hard.  I suspect none will work, but won't know until you try.  In fdisk and parted, the partition type would be "Linux", not ext4.  Then you'd use mkfs -t ext4 to create the file system.  If it were me and I didn't want to use LVM, I'd make 3 partitions.
/ - 25G ext4 for the OS and applications
swap 4.1G - the only size I use for laptops/desktops (non-servers). use the **mkswap** command.
/home - 50G or so. I'd leave the rest of the disk unused, for now.

While I was at it, I'd use a GPT, not MSDOS/MBR partition table.  If I wanted to use LVM, I'd do things very differently.

I tried to create a new partition table and a new partition with both **fdisk **and **parted**, and then create the filesystem with **mkfs**. I got the same result with both:
```

ubuntu@ubuntu:~$ sudo mkfs -t ext4 /dev/sda1
mke2fs 1.44.1 (24-Mar-2018)
Discarding device blocks: done                            
Creating filesystem with 58607505 4k blocks and 14655488 inodes
Filesystem UUID: bb54474e-9f7a-4f28-ac06-d4bc87442943
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information:          
Warning, had trouble writing out superblocks.

```

So no luck there... :/

> **TheFu said:**
> But as for doing the installation, there usually isn't any need to pre-partition. Do that inside the installer, to it will handle legacy or UEFI setup for you. I see that isn't working for you and it is the reason you are here.  The installer doesn't use fdisk or parted or gparted to do partitioning, so it is likely some sort of hardware issue.

Tomorrow I'll check the SSD on another computer... but there is something that is driving me crazy: I tried to install windows again and somehow the installation has no issues... How is this possible???

---

### Post by TheFu on 2019-10-01
If the BIOS doesn't have anything mentioning SMART, I highly suspect that is one of the cheapest BIOSes made. There isn't anything that can be done, for a laptop. Sorry.
If it was a desktop, you could swap out the motherboard for a more capable version almost certainly.
And you could take the SSD to another computer with SMART capability and look through the data there.  I don't know if the data from any faults on the laptop will show up. All my systems have SMART capability and I always ensure it is enabled.  I also ensure I only buy systems that support VT-x/AMDv. Call it a personal bias.

Driver support by vendors for Windows is something every vendor strives to ensure. Many vendors don't test with Linux at all, so if they never intend for Linux to work, it is easily possible that it won't, on their low-low-end equipment.  Just because something works on Windows, doesn't mean it doesn't have hardware faults.  For decades, Windows has ignored hardware faults that other OSes do not ignore.  I've seen this since my days with OS/2.  Properly checking hardware makes booting slow, so MSFT has definitely gotten worse about it over the decades. I am not very impressed when something works in Windows.

I hope the issue is just a bad SSD and nothing else. That would be the easiest problem to replace.

By any chance have all the partition sizes been the same that you've tried to create?  Perhaps trying a different size would cause different blocks to be involved?

---

### Post by en3rg1zer on 2019-10-02
> **TheFu said:**
> Driver support by vendors for Windows is something every vendor strives to ensure. Many vendors don't test with Linux at all, so if they never intend for Linux to work, it is easily possible that it won't, on their low-low-end equipment.  Just because something works on Windows, doesn't mean it doesn't have hardware faults.  For decades, Windows has ignored hardware faults that other OSes do not ignore.  I've seen this since my days with OS/2.  Properly checking hardware makes booting slow, so MSFT has definitely gotten worse about it over the decades. I am not very impressed when something works in Windows.

Damn... I really hate that OS... This whole thing was about trying to get my girlfriend into linux (it's her laptop). Now I'm starting to feel like we won't be that lucky... :/

> **TheFu said:**
> I hope the issue is just a bad SSD and nothing else. That would be the easiest problem to replace.

I'll check it today on a different machine and post something here afterwards.

> **TheFu said:**
> By any chance have all the partition sizes been the same that you've tried to create?  Perhaps trying a different size would cause different blocks to be involved?

Actually no. The first time I tried installing ubuntu I gave him a 50GB partition for the OS. Then I realized it was probably way to much and started giving him only 25GB. The only partition that has remained the same has been the swap (I always make it 4GB at the end of the memory).

---

### Post by TheFu on 2019-10-02
Not that it helps you, but I woke up to this email today:
```
This message was generated by the smartd daemon running on:

   host name:  hadar
   DNS domain: example.foo

The following warning/error was logged by the smartd daemon:

Device: /dev/sda [SAT], 2 Currently unreadable (pending) sectors

Device info:
WDC WD10EZEX-00RKKA0, S/N:WD-WMC1Sxxxxxx4, WWN:5-0014ee-xxxxxxxxdcd, FW:80.00A80, 1.00 TB
```
It is an old WD-Blue from 2012-ish, only used as a scratch disk.  It was an OS disk in a machine I removed from service in Feb and sold (too cheap) in June.  Only 1 SMART parameter is bad and there should be plenty of other sectors for the relocation to occur, but that hasn't happened. I've tried to let the disk find and automatically relocate those sectors this morning after taking the partition out of read-only mode, twice.  Other partitions on the same disk aren't showing any issues and are still mounted read-write.  I didn't expect that.  Running **badblocks** on it now, hoping to force the relocation.

---

