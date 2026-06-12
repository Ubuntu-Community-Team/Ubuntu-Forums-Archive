---
title: "Unable to boot following attempted dual boot install"
date: 2020-07-03
forum: Installation &amp; Upgrades
---

### Post by mark-wootton on 2020-07-03
[COLOR=#1A1A1B][FONT=&amp]I tried to install Ubuntu 20.04 on a Windows 10 machine as a dual boot. At the end of the process, there was an error message telling me that the installation had failed. Rebooting the machine, I can't boot to either OS, and I now see:[FONT=&amp]
[/FONT][/FONT][/COLOR][FONT=&amp]```
[FONT=&amp]Reboot and select proper Boot device
[/FONT][FONT=&amp]or Insert Boot Media in selected Boot device and press a key[/FONT]
```[/FONT]
[COLOR=#1A1A1B][FONT=&amp]This is how I got here:
[/FONT][/COLOR]
[LIST=1]
[*][FONT=inherit]I shrank my Windows partition to make space from within Window. No problem encountered here.
[/FONT]
[*][FONT=inherit]I loaded a Ubuntu live USB
[/FONT]
[*][FONT=inherit]When I got to the disk partition screen I created partitions in the free space for "/”, "swap space", "EFI", and "/home" in that order.
[/FONT]
[*][FONT=inherit] I [/FONT][FONT=inherit]let the process run, it failed, and now I can't boot to either Windows or Ubuntu.[/FONT][FONT=inherit]
[/FONT]
[/LIST]
[FONT=inherit][/FONT][COLOR=#1A1A1B][FONT=&amp]I imagine I've must have made a simple error along the way. What have I screwed up?[/FONT][/COLOR]

---

### Post by mark-wootton on 2020-07-03
Update: I&#8217;ve restored the Windows boot loader. It seems it&#8217;s using MBR, thus my problem. I&#8217;m looking to get the dual boot working now. Suggestions are very welcome.

---

### Post by davidcbryant on 2020-07-03
> **mark-wootton said:**
>  ... [COLOR=#1A1A1B][FONT=&amp]I imagine I've must have made a simple error along the way. What have I screwed up?[/FONT][/COLOR]

It's hard to tell from your brief description. But you probably messed everything up by creating a second EFI partition. Can you boot a "live" system from a USB  stick (the Ubuntu installation medium is probably OK), get to a terminal prompt as root, and then say

[FONT=courier new]root # fdisk -l[/FONT]

You'll get a list of all the disk devices in your system, along with  partitioning info. Post the partition table here, and somebody may be  able to help you. Oh -- do you know how to look at your BIOS? You can  (maybe) boot into Windows by changing the default boot device / device  manager. It would also be good if you mentioned what sort of computer  you have, and what kind of disk. Conventional SATA hard disk? SCSI? SSD?

Your system is probably installed on your first disk drive, so you might also try saying

[FONT=courier new]root # fdisk -l /dev/sda[/FONT]

if the first command generates reams of output. Oh -- how familiar are you with the Linux console? How about the Windows command prompt (also known as a DOS box)? The Linux console / terminal is similar to a DOS command prompt, but most of the commands are not the same in Linux as they are in Windows / DOS.

David Bryant
Canyon Lake, Texas

---

### Post by mark-wootton on 2020-07-03
I've managed to get back into Windows by restoring the boot loader from  an install disk. Apparently the harddrive is set to use MBR, not EFI. I  believe its a SATA. It's definitely not a SSD.

Here's the output of the terminal command you suggested:

```
ubuntu@ubuntu:~$ sudo fdisk -l
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


Disk /dev/sda: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000DM001-1ER1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xab7ec381

Device     Boot      Start        End    Sectors  Size Id Type
/dev/sda1  *          2048    1026047    1024000  500M  7 HPFS/NTFS/exFAT
/dev/sda2          1026048 3701124497 3700098450  1.7T  7 HPFS/NTFS/exFAT
/dev/sda3       3905925120 3907022847    1097728  536M 27 Hidden NTFS WinRE
/dev/sda4       3701125118 3905925119  204800002 97.7G  5 Extended
/dev/sda5       3701125120 3749953535   48828416 23.3G 83 Linux
/dev/sda6       3749955584 3765954559   15998976  7.6G 82 Linux swap / Solaris
/dev/sda7  *    3765956608 3766454271     497664  243M ef EFI (FAT-12/16/32)
/dev/sda8       3766456320 3905925119  139468800 66.5G 83 Linux

Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.




Disk /dev/sdb: 3.74 GiB, 4000317440 bytes, 7813120 sectors
Disk model: Cruzer          
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x15f006ae

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 5303231 5303232  2.5G  0 Empty
/dev/sdb2       4222640 4230575    7936  3.9M ef EFI (FAT-12/16/32)
/dev/sdb3       5304320 7813119 2508800  1.2G 83 Linux
```

Thank you for your help.

---

### Post by mark-wootton on 2020-07-03
> **davidcbryant said:**
> 

if the first command generates reams of output. Oh -- how familiar are you with the Linux console? How about the Windows command prompt (also known as a DOS box)? The Linux console / terminal is similar to a DOS command prompt, but most of the commands are not the same in Linux as they are in Windows / DOS.



I am fairly comfortable using command line interfaces, be that on Windows or Linux.

---

### Post by oldfred on 2020-07-03
Remove boot flag from sda7 as you can really only have one working boot flag per device.
And then convert UEFI install of Ubuntu to BIOS boot install, just by reinstalling grub.
UEFI uses grub-efi-amd64 and BIOS uses grub-pc.

Often easier to just use Boot-Repair from Ubuntu live installer booted in BIOS mode. Not sure if auto fix will want suggest to install grub-pc or you have to use the Advanced mode.

But make a Windows repair/recovery flash drive.
Booting Windows 10 in BIOS mode on same drive with another system has a bit of a hassle. Windows with updates turns fast start up back on or if Windows needs chkdsk, grub will not boot Windows. Then you have to directly boot Windows. And have to temporialy install Windows boot loader, boot Windows & fix issue & then restore grub to MBR. 
Always keep Windows repair/recovery flash drive and Ubuntu live installer flash drive handy.

With UEFI, its like having two or more MBRs and you can have as many boot loaders as you want. Then when grub does not boot Windows, you just reboot & boot Windows directly from UEFI boot menu.

Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012.BIOS install is more for compatibility on older systems or large commercial users with many systems who wanted same configuration across various models of systems, some older & BIOS.

---

### Post by mark-wootton on 2020-07-04
Solution: Before letting the live USB load, open the boot load menu (by F12, in my case). The USB was listed twice. Selecting the non-UEFI option results in the installer working normally and completing successfully. I'm typing this from with Ubuntu now. Thanks everyone for your help.

---

