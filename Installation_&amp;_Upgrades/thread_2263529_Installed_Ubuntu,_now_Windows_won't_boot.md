---
title: "Installed Ubuntu, now Windows won't boot"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by joseph46 on 2015-02-01
HP Compaq 6910p - Intel Core 2 Duo CPU T7300 @ 2Ghz 2GB Memory

There are a handful of threads on Ubuntu forums here and elsewhere that I've read, tried, etc., nothing seems to work or match my situation.

I had 2 partitions (C and D) with Windows installed on one (C). I decided to try Ubuntu.  I moved the few misc. files on D and on to C then installed Ubuntu 10 on D (I bought the computer from a friend and it always had these 2 partitions).  When everything was finished, I noticed grub facilitated the dual boot. Ok. Ubuntu boots fine. It was great. I tried to go into windows from grub and all I got was a black screen with a blinking cursor at the top left.  I ran boot repair from Ubuntu (yannubuntu).  Nothing.  Tried something else, then I couldn't even get into Ubuntu.  Ran from USB live and ran boot repair.  Then Ubuntu works again but still no Windows.

My software developer linux-using brother looked at the C drive from the Linux terminal and said everything is still there.  He ran a few commands... then once again we couldn't get back into either Ubuntu or Windows.  LiveUSB + Boot repair ran again and Ubuntu is back.  I figure if I uninstall Ubuntu completely from the LiveCD using OS-uninstaller.  It works. No more grub either, but the computer just boots straight to the blank screen with the flashing cursor now...

I have a handful of installation disks most are things like a 180-day trial version of Windows Server 2003, windows 7 64 bit, finally one that may be XP SP2 (I think 32 bit).  I tried 2 or 3 of them and I get the same error shortly after the CD boots and I try to "recover" using installation disk.  It says that "Setup did not find any hard disk drives installed in your computer."  Searching that, every place says drivers have to be loaded by hitting f6 before an OS tries to boot.  There is no such option on my computer.  I've changed several BIOS settings and nothing ever changes anything to fix, so I've restored everything to default.

What did the Ubuntu installation do and any advice on getting Windows XP to boot again?

---

### Post by oldfred on 2015-02-01
May need to see details just to see if configuration looks ok.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Have you run chkdsk from the Windows repair console on all NTFS partitions? Is boot flag on the partition with the boot files?

---

### Post by joseph46 on 2015-02-01
I booted up Ubuntu back with a live USB.  Here is the link from BootInfo:
[http://paste.ubuntu.com/10002642/](http://paste.ubuntu.com/10002642/)

Looking at that thing, sda5 used to be linux before I removed it.  It formated to NFTS when I got rid of it.  Not sure why it says Vista although the computer has a Vista sticker on it, indicating that it was shipped with Vista.

I can't run chkdsk because even when I use an installation disk to go into the blue menus / pre-installation / loading drivers to prepare the installation etc., it gives me an option to enter the Recovery Console but as I said before, I get this error: [COLOR=#000000]"Setup did not find any hard disk drives installed in your computer."[/COLOR]

---

### Post by yancek on 2015-02-01
The only sign of Ubuntu showing in the Boot Repair Summary is on the 8GB Sandisk flash drive.   You have an Ubuntu Live CD on the flash drive created with the unetbootin software that can be run as a Live system or used to install Ubuntu.  So, you do not have Ubuntu installed to the hard drive.  You do have your windows partitions on the hard drive but you have the syslinux bootloader in the MBR instead of windows code.  Not sure how that would work or if it would.

If you had an xp installation CD you could repair the mbr.  Maybe someone a little more familiar with windows and xp will post.

---

### Post by joseph46 on 2015-02-01
> **yancek said:**
> The only sign of Ubuntu showing in the Boot Repair Summary is on the 8GB Sandisk flash drive.   You have an Ubuntu Live CD on the flash drive created with the unetbootin software that can be run as a Live system or used to install Ubuntu.  So, you do not have Ubuntu installed to the hard drive.  You do have your windows partitions on the hard drive but you have the syslinux bootloader in the MBR instead of windows code.  Not sure how that would work or if it would.

If you had an xp installation CD you could repair the mbr.  Maybe someone a little more familiar with windows and xp will post.

At this point, I'm just trying to get XP bootable.  I intentionally uninstalled Ubuntu to try to get XP to boot as it hasn't since I installed Ubuntu a week ago.  You're right. It doesn't work.  I'm not sure why installing Ubuntu screwed up the MBR.  I have installation disks but can't use repair for the reasons described above.  I wish there was some way to repair it without going through windows also.

---

### Post by yancek on 2015-02-01
Installing Ubuntu didn't "screw up the mbr", the default installation is to install the Grub boot code to the master boot record.  That information is shown on the Installation screen explicitly and labelled "Device for bootloader installation".  If you left the default, that's what happened.  The difference between Linux/Ubuntu and windows is that windows will do the same but will not ask you nor will it inform you.  Also, although some Grub code is in the master boot record, most of the boot code necessary to boot is on the system partition, you know, the one you deleted.  You went about this backwards.  You need to change the boot code to windows before deleting the Linux partition. 

Windows is proprietary code and which is why you need to go through microsoft/windows.  Nothing anyone else can do about that.

---

### Post by joseph46 on 2015-02-01
> **yancek said:**
> Installing Ubuntu didn't "screw up the mbr", the default installation is to install the Grub boot code to the master boot record.  That information is shown on the Installation screen explicitly and labelled "Device for bootloader installation".  If you left the default, that's what happened.  The difference between Linux/Ubuntu and windows is that windows will do the same but will not ask you nor will it inform you.  Also, although some Grub code is in the master boot record, most of the boot code necessary to boot is on the system partition, you know, the one you deleted.  You went about this backwards.  You need to change the boot code to windows before deleting the Linux partition. 

Windows is proprietary code and which is why you need to go through microsoft/windows.  Nothing anyone else can do about that.

Thanks for sharing the knowledge.  It's making more sense.  So is it possible to "retrace my steps" by reinstalling Ubuntu and then somehow fix things?

---

### Post by leclerc65 on 2015-02-01
Your 8G card complicates matter.
I would pop it out before trying anything.

---

### Post by joseph46 on 2015-02-02
So I'm reinstalling Ubuntu from Live USB.  I think I've reached the magic question... Should I choose "Device for boot loader installation:"

1. /dev/sda ATA ST940210AS (40.0 GB) ----This is the entire hard drive
2. /dev/sda1 Microsoft Windows XP Professional ---- XP partition, C drive, presumably
3. /dev/sda5 ------- that D drive partition that I had previous set up Ubuntu on.

Not sure which option I chose last time.

Which should I choose?  Probably the 1st?

---

### Post by leclerc65 on 2015-02-02
I would choose #1.
Also , if you choose to install from the SD card, check the BIOS to see if the HDD boot first - press the del, ESC, F2, F12... depending on the computer, to boot from the card if required.

---

### Post by yancek on 2015-02-02
The first option will install the Ubuntu Grub bootloader to the master boot record of the primary drive, sda on which you have Ubuntu and xp.  It should then create entries to boot both Ubuntu and xp.  Do not select the second option as that will likely overwrite your windows boot files and you won't be able to boot it. Selecting the third option will put the boot files on the Ubuntu partition and then you will either need to reinstall Grub to the mbr or manually configure the windows boot files to boot Ubuntu.  Good luck with that.

First option is best.

---

### Post by oldfred on 2015-02-02
Never ever install grub to a NTFS partition. We filed a bug report years ago that the installer should not even offer that option.
Windows has essential boot information in the partition boot sector that has partition size info that must match partition table and info on which boot loader ntldr for XP or bootmgr for all later versions. 
If boot sector says Vista, it may be the newer boot sector specifying bootmgr, but if XP you need to restore the version that specifies ntldr. From newer Windows repair CD or flash drives you can use bootsect.exe.
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

