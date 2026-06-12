---
title: "Dual Boot With Win 7 Installed on /dev/sda2 (2nd partition of HDD, Drive D:)"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by bizhat on 2013-04-04
Hi,

I had a Windows XP installed on my Drive C: (/dev/sda1).

Later i installed Windows 7 on Drive D:, another partition on same disk (/dev/sda2).

I have deleted all files on Drive C (/dev/sda1), which had Windows XP installation. Edited boot menu, so i only Windows 7 boot options shows up.

Since drive C: was first active OS installation, i think the boot records are there ?

If i format drive C and install Ubuntu on it, will i able to multi boot between Win 7 installed on Drive D:  (/dev/sda2) ?

Thanks,

Boby

---

### Post by oldfred on 2013-04-04
If sda1, your XP install was the active partition or had boot flag, all the Windows 7 boot files were in sda1. Did you copy them to sda2  before deleteing sda1? Or did you install Windows 7 with the boot flag on the sda2 partition. If boot files are missing, grub will not find the Windows 7 install as it is missing its boot files. If boot files are in Windows 7 and it currently boots, then you can install Ubuntu and dual boot. If resizing Windows 7 partition do it from Windows 7's disk tools, but do not create partitions with Windows 7 as it may convert to dynamic partitions which do not work with Linux.

       Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by bizhat on 2013-04-04
> **oldfred said:**
> If sda1, your XP install was the active partition or had boot flag, all the Windows 7 boot files were in sda1. Did you copy them to sda2 before deleteing sda1? 

Thanks @oldfred for the reply. 

I have not deleted it yet. Is there anyway i can make windows 7 partition to boot or copy boot records to Win 7 partition (It is drive C in the image, that is sda4, not 2)

Here is my disk partition as you can see from Windows 7 disk management

[http://webhostingneeds.com/yujin/drives.png](http://webhostingneeds.com/yujin/drives.png)

The drive E is where i have active OS before.

---

### Post by oldfred on 2013-04-04
Do not create any partitions with Windows as that may convert to dynamic and cause real issues.

You should be able to just copy boot files.

       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Your view shows it as a logical drive. Windows will not boot from logical partitions. You have to reinstall to a primary, convert to a primary or maintain a small primary boot partition with the boot files. Which ever partition has boot files has to be the active partition or have the boot flag from gparted.

You also may have to run chkdsk from Windows 7 on the Windows 7 partition. There are two different PBR - partition boot sectors. Windows 7 should be correct, but a chkdsk should not hurt.

---

### Post by bizhat on 2013-04-05
@oldfred Thank you very much for the reply. I have to wait until i reinstall win 7.  Before it was possible to install ubuntu inside windows folder, this is not possible now ?

---

### Post by nerdtron on 2013-04-05
> **bizhat said:**
> Before it was possible to install ubuntu inside windows folder, this is not possible now ?

It is still possible by using Wubi. Just insert your Ubuntu CD (or mount it on a virtual drive) while you are in Windows 7. But I suggest you do a full install if you plan to use Ubuntu in the long run.

---

### Post by oldfred on 2013-04-05
With 13.04 they are dropping support of wubi. I think part of the reason is wubi does not work with the new gpt partitioned drives that are used with UEFI. And all new computers are now UEFI, so a user with a new computer cannot now use wubi.

wubi still is available with 12.04, but you have to have a BIOS install with MBR(msdos) partitioning. It also now has to be installed from inside Windows not from a CD/DVD/Flash like the normal partitioned installs.

---

### Post by bizhat on 2013-04-06
I checked wubi on ubuntu-12.10-desktop-i386, but it did not show the install inside folder option. Only option i see was to reboot to live CD.  What if i  made the 250 GB HDD (i have 2 HDD on my pc, 250 GB is used for backup, i will be getting another 1 TB HDD for backup) as boot disk in bios, then install Ubuntu in it, will the setup take the Win 7 Install on other disk ?

---

### Post by oldfred on 2013-04-06
If you have multiple drives, I always suggest installing an operating system on every drive. I have Ubuntu on several drives and my old XP install on one that is not used except for backup on another partition on that drive.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

With two drives you should not use auto install options as they will install grub2's boot loader to sda.
      
 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by bizhat on 2013-04-08
Thank you very much for the reply. I will go through the links you provided.  Please mark the thread as SOLVED.

---

