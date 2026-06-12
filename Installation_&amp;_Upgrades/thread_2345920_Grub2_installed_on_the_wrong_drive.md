---
title: "Grub2 installed on the wrong drive"
date: 2016-12-09
forum: Installation &amp; Upgrades
---

### Post by jaimelesoul on 2016-12-09
Hello,

I am attempting to install Ubuntu on one of my numerous hard drives, but have encountered difficulty in that what is referred to as "grub2", which I gather is what is used to allow me to pick where to boot from, is located on drive number 1, whereas the actual main installation of Ubuntu that I am currently using to type this is located on drive number 2. This is problematic in that I can't keep drive number 1. After much frustration and gnashing of teeth I have decided to seek out your help. I would greatly appreciate if someone could walk me through how to transfer everything necessary to run the OS onto drive2. Thanks in advance and I apologize if I say anything stupid, I know nothing about computers.

---

### Post by yancek on 2016-12-09
Every operating system has defaults for an installation and your install is a non-standard install, you want to install to a secondary drive.  In order for the installer to be aware of this, the person installing must inform it.  Ubuntu has several installation options and the one you would need to select is the manual, referred to as Something Else in Ubuntu.  Using this option, you can select which drive to install the Grub bootloader to.  You don't mention any other operating system which could complicate matters?  Also, is this a newer computer with UEFI with another OS on the first drive?  If you have another operating system on the first drive, what is it?  Also, what does 'can't keep the first drive mean'?

---

### Post by oldfred on 2016-12-09
If BIOS, you must use Something Else and in partitioning screen choose which drive's MBR to install the grub2 boot loader into.

If UEFI, you must partition in advance using gpt and be sure to have ESP - efi system partition as first partition on drive. But grub will not install into it, but into the ESP on drive seen as sda. You then can copy files from ESP on sda to ESP on sdb. But may need to update UEFI with correct location.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[URL="http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond"]http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond

[/URL]
 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL] 

[URL="http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond"]
[/URL]

---

