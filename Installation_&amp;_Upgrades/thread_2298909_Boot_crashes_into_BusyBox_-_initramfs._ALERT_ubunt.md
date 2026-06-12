---
title: "Boot crashes into BusyBox - initramfs. ALERT ubuntu--vg-root does not exist"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by paul-schulinck on 2015-10-14
A year and a half ago, I installed Ubuntu 14.04 LTS on a 1 TB harddisk which I solely use for Ubuntu. During the installation I opted to encrypt the disk (which I regret afterwards because I read of the problems that arose in several cases). 
In BusyBox/Initramfs the message was "ALERT! /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell! I read at least one topic here in ubuntu forums that was speaking about the same error, but the conditions of the user's PC were different than the setup in my PC, that's why I posted this new thread.
If I, after the crash into initramfs, issue the command "vgchange -ay" followed by the command "exit" then Ubuntu 14.04 LTS boots OK. lvm2 is installed.
I created various images / screenshots. See my dropbox folder: [https://www.dropbox.com/sh/aemzvhlj2m9blmn/AACH4r2sQKNQCuy5KHisYsDHa?dl=0](https://www.dropbox.com/sh/aemzvhlj2m9blmn/AACH4r2sQKNQCuy5KHisYsDHa?dl=0) 

Notes: 
1) my desktop PC standard boots into Windows 10 Pro, which is installed on another harddisk. The Ubuntu installation I choosed at boot-time via Shift-F8 menu and then select the proper disk on which Ubuntu is installed /dev/sdc1 (/boot). The root partition is on (/dev/sdc5);
2) Before I installed ubuntu, I disconnected my other disks: boot-SSD and a 2TB harddisk used as /data disk when running Windows10. I had bad experiences in the bast with dual-boot systems. I was afraid that the MBR on the Windows boot partition would be changed when installing Ubuntu. That's why maybe a confusion was created. As a result of this, in /etc/fstab is a line that says: "# /boot was on /dev/sda1 during installation"
3) The drive where ubuntu is installed on is: ATA ST1000LM014-1EJ1 (scsi), sdc;
4) in /boot/grub/grub.cfg I see various lines that contain parts like this: "-set=root --hint-bios=hd2,msdos1". Is this correct? As far as my knowledge goes: "hd0 = sda", "hd1 = sdb" and "hd2 = hdc". So the hd2 reference would be OK, I think.

I would appreciate very much your help. I am not very experienced in the Linux OS, although since a year or six I am doing my best to improve my knowledge.

---

