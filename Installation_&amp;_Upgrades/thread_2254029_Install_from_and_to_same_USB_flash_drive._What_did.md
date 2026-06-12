---
title: "Install from and to same USB flash drive. What did I do wrong? [UEFI]"
date: 2014-11-24
forum: Installation &amp; Upgrades
---

### Post by Bejamin_Hastings on 2014-11-24
_Situation_
I would like to install Ubuntu on a USB flash drive. Further, the computer has no optical drive or other storage device (HDD or SSD). I have only one flash drive available, of 8 GB size. Firmware is set to boot only UEFI in Secure Boot.

_Idea_
On the IRC I got some sound advice: Create a small partition from which to install from.

_Progress (in the works, please help)_
Using a different Computer, running Windows 8, I prepared the flash drive. I cleaned it from all partitions, formatted it in MBR format and created a 1.5 GB FAT32 partition.  I let the LiLi USB creator (Linux Live USB Creator) do its magic. (to make it bootable and to put the 14.10 x64 ISO files onto the FAT32 partition I presume).

With this bootable flash drive I went to the target computer, booted and chose the installation option.
At that point the partitions looked like
1 Ubuntu Install (x64 14.10 image), FAT32, 1.5 GB
2 free space, some 6 GB

The installer forced me to partition manually which I did like this
1 Ubuntu Install (x64 14.10 image), FAT32, 1.5 GB
2 mount as /, ext4, some 5 GB
3 swap, 0.5 GB
4 empty, FAT32 some 0.5 GB, (in case I insert the drive in a computer running Windows)
bootmanager on SDA (not SDA1 or something else)

Everything went well until the reboot. I keep getting into the "install image boot" i.e. I am given the option to boot it as 'live' or to install (which I just did)

_What went wrong?_
Missing EFI partition?
Boot manager installed in wrong location?
No proper UEFI install at all? (UEFI computer usually show some UEFI entry in BIOS but it is only giving me the flash drive as such, just like it did before I did the installation).
Boot manager just falsely pointing to the install partition instead of pointing to the ext4 partition?
Something else?

---

### Post by sudodus on 2014-11-24
Welcome to the Ubuntu Forums :-)

What you try to do is possible but quite advanced (to install into the same partition as you boot from). Unless you have a lot of experience of linux, I would suggest that you try some other method, for example to use the 6 GB free space for a casper-rw partition and create a ***persistent live USB drive***. It will use an overlay system, so that you can install program packages as well as store personal data files. But you cannot update/upgrade the linux kernel. There are several descriptions of the method, for example in Ubuntu Forums posts by *C.S.Cameron*, and also in the following links (and links from them)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]                 

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

