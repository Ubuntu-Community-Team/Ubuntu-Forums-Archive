---
title: "Boot And Run Ubuntu 13.04 On External Hard Drive?"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by CharleyGnarlyP290 on 2013-05-04
I have given up trying to do a dual boot system on my computer due to the whole UEFI/ BIOS stuff... a little too complicated to me. This is my primary computer and can't risk messing something up on Windows 7.
So... I have an external USB hard drive I would like to install UBUNTU to and be able to run it from there. My questions are these:
1. How do I install UBUNTU 13.04 to the external drive?
2. How do I run UBUNTU from the external drive?
I have searched high and low, but can't seem to find a definitive answer. All of the GRUB/ Grub 2 stuff is Greek to me. I mention this because I see it brought up quite a bit in my searches.
Thanks for any help that can be provided. Step by step, links, anything will do.

My computer is an HP Pavilion i3-2120 CPU running at 3.3 GHz with 8 gigs of RAM.

---

### Post by oldfred on 2013-05-04
Is your computer UEFI booting with Windows 8 and secure boot?
Edit - I missed you mentioned Windows 7. Then you do not have secure boot, but are you booting with BIOS or UEFI? That is critical to how to install to external.

Then it still is complicated, however you do it. Thank you very much for Microsoft and secure boot.

Almost all the instructions for installing to a second drive USB or internal or flash drive are for BIOS/MBR. And if you want you can dual boot with Ubuntu in BIOS and Windows in UEFI. It just is not easy as if you want Winodws you have to go into UEFI, turn on UEFI and maybe secure boot and boot Windows. Then  to boot Ubuntu you have to go into UEFI/BIOS turn off secure boot, turn on BIOS/CSM/Legacy boot and boot from external.

Or you can do the more complicated UEFI install to a second drive. Several have done it, but second drive has to be gpt partitioned with an efi partition first and the partitions you want for Ubuntu.

       Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by CharleyGnarlyP290 on 2013-05-04
I am booting in UEFI mode.
When I go into my boot menu at startup, my external drive is listed. Would I be able to just open the boot menu at startup and select which drive to boot from?

---

### Post by oldfred on 2013-05-04
I do not know if it switches from UEFI to BIOS of your install on external is BIOS based. Much easier dual booting if both are UEFI, but initial set up is more difficult.

Do you have external drive gpt partitioned with an efi partition first? Then you could just add Ubuntu /, /home & swap installing in UEFI mode and it would work.
IF you have data converting to gpt may erase all of it. There is a program that may convert, but backups still required.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

              I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

    
 Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[URL="http://ubuntuforums.org/showthread.php?t=1718966"]http://ubuntuforums.org/showthread.php?t=1718966

[/URL] Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

[URL="http://ubuntuforums.org/showthread.php?t=1718966"]
[/URL]

---

### Post by CharleyGnarlyP290 on 2013-05-04
Thanks for the replies oldfred. Most of what you explained is way over my head though.
As far as my external drive goes, there is nothing on it and I can do whatever I need to it. What should I do to it before installing UBUNTU to make it compatible?
Step by step or a link to step by step would be appreciated. The drive is a clean 148 GB.

---

### Post by oldfred on 2013-05-05
Best to partition in advance.
I have BIOS but use gpt. I have created my gpt partitions with gparted.  Under device, create partition table, advanced, choose gpt not the  default msdos (MBR) partitioning.

Then add all the partitions I show above for both a gpt and both gpt or MBR configuration. If you want part of drive for NTFS create that also. Keep track of which partitions are planned for / and /home (I have made the mistake of using the wrong one.

Then boot the USB flash drive installer in UEFI mode from UEFI menu, not BIOS/Legacy mode. You can install grub boot loader to the internal hard drive's efi partition, later  we may want to copy files to external.
You have to use Something else or manual install and specify mounts / and formats - ext4 and /home and ext4. It should find swap on its own.

---

