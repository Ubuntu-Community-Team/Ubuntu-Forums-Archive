---
title: "Cannot uninstall 10.10 and Grub"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by mshipon on 2010-11-04
I installed Ubuntu 10.10 along with my Windows 7 operating system. After quite a bit of trial and testing, I've decided to remove Ubuntu.  I probably did this incorrectly, but I deleted the Ubuntu partition from within Windows 7 partition manager.  The next time I booted the system, the computer tried booting with Grub and failed due to not finding the partition.

I've since reinstalled Ubuntu just to be able to dual-boot again.  How do I cleanly remove Ubuntu and the Grub boot manager?

Thanks!

Martin

---

### Post by ezsit on 2010-11-04
I believe you will need a Windows 7 installation CD/DVD to boot from after deleting Ubuntu and repair the master boot record (mbr) so that Windows will boot again. You will have to get confirmation from a Windows 7 user though.

Here is a link to Windows 7 recovery media:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by garvinrick4 on 2010-11-04
If you do not have a Windows installation or repair disk:
In a live Cd of Ubuntu: open a terminal:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
delete ubuntu in gparted
Boot into Windows on HDD.
If have a windows disk; Follow guide in this link
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by oldfred on 2010-11-04
ezsit is correct,  and if you are a windows user it is the best way as you need to know how to repair windows and have a windows repair CD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

BootRec.exe /fixmbr


But from Ubuntu or most linux repair CD's you can install a generic boot loader that works just like windows in the MBR.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by ezsit on 2010-11-04
> But from Ubuntu or most linux repair CD's you can install a generic boot loader that works just like windows in the MBR.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

That's fantastic! I never knew you could just install old reliable lilo to boot windows. Cool!

---

