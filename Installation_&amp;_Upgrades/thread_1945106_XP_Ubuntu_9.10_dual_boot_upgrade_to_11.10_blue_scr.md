---
title: "XP Ubuntu 9.10 dual boot upgrade to 11.10 blue screens XP"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by jwill911 on 2012-03-22
Hi, First time poster here.

I  have a working dual boot installation XP/Ubuntu 9.10 I installed 11.10 and afterwards XP blue screens. During the install the XP install is recognized and I was presented with three choices; I chose the first, default "Install along side XP".

As I mentioned attempting to boot XP I get a quick flash of blue screen then reboots, obviously the boot sector got damaged in some way.  This is a lab machine and I had a G4U image of the install so I re-imaged but wonder what went wrong or what I could have done wrong.

Any clues would be appreciated before I try it again?
Thanks in advance,
John Williams

---

### Post by oldfred on 2012-03-22
Welcome to the forums.

We need to see the details of your configuration. Perhaps some Windows file is missing, but once grub passes booting to Windows it usually is a Windows issue.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Sometimes a chkdsk is required, and that can only be run from your XP CD. Just about everything else can be done from Ubuntu or most Linux repairCDs.

---

### Post by jwill911 on 2012-03-22
Hi, Thanks for replying.

I replicated the problem; had to reinstall 11.10 verified the same issue then installed boot-repair.

Here's the link referenced in boot repair:
[http://paste.ubuntu.com/895601/](http://paste.ubuntu.com/895601/) on the boot-info and 895640 after the boot-repair said it was successful but wasn't.

Appreciate the help.
John Williams

---

### Post by oldfred on 2012-03-22
Reinstalling Ubuntu will not change the Windows issues. Once grub has passed booting to Windows it is not different than the chainload the the Windows boot loader in the MBR does in chain loading to the NTFS partition boot sector.

Boot script just checks that NTFS boot sector looks normal, but it can have internal issues or something else is wrong. Normally you do not get a menu entry if you have major issues.

Some are able in some versions of Windows get to repair console by pressing f8 at almost the same time they press the grub entry for Windows. It is a bit quicker than the boot from a MBR, so it often is difficult to be quick enough.

Otherwise use Windows CD to run chkdsk and possibly fixBoot.

If you run the fixMBR command you will have to reinstall grub2's boot loader to the MBR. So have a Ubuntu liveCD handy.

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by jwill911 on 2012-03-23
Hi, Thanks again for the help.  I followed your advice installed boot-repair but it was of no help.  Must be an issue with Windows although it's strange the dual boot image with XP and Ubuntu 9.10 works fine until I upgrade to 11.10 :confused:  I actually have 8 of these identical machines in a rack I use for testing.  I'm sort of between testing cycles and wanted to upgrade one unit with all the latest burn an image then image each of the others. 

I feel like this thread can be put to sleep if I come up with a new issue I'll repost.

Oh forgot to mention I'm just loading a clean copy of XP and setting up dual boot from scratch with all the updates.

Thanks,
John Williams

---

### Post by jwill911 on 2012-03-26
Hello, I know this thread is "solved" but I thought I'd add the final note.  You were absolutely correct with your statement Windows was corrupted.  I booted from the Windows install CD ran "R" recovery, chkdsk, fixboot, then Windows booted normally and I am off and running creating an updated disk image to update all my lab PCs.

Thanks again,
John Williams :p

---

