---
title: "Ubuntu 14.04 not booting with Windows 7"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by joshisapan on 2014-04-23
I upgraded from ubuntu 13.10 to 14.04 few days back, but the system is not booting in regular fasion. I have to go to recovery mode then select install grub and then select regular install to install 14.04. 

the message displayed after normal boot is 

mount: mounting /dev/loog0 on /root failed: Invalid argument
mount: mounting /dev on root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed No such file or directory
Target filesystem dowsn't have requested /sbin/init.
No init found. Try passing init=bootarg

My blkid looks like this- 

pc@ubuntu:~$ sudo blkid
[sudo] password for pc: 
/dev/sda1: LABEL="System Reserved" UUID="1EBCF85DBCF830BF" TYPE="ntfs" 
/dev/sda2: UUID="42E6965DE6965151" TYPE="ntfs" 
/dev/sda3: UUID="D662846A628450E3" TYPE="ntfs" 
/dev/loop0: UUID="6a8c0b1f-4ffc-4160-858a-67ae4146372d" TYPE="ext4" 
/dev/sda4: UUID="DEF06280F0625EB1" TYPE="ntfs" 
/dev/sdb1: LABEL="sapan" UUID="A008-C57A" TYPE="vfat" 

The last one is my pen dirve. After booting it either goes to shell prompt or says "Serious errors while booting /" and gives me options of i to ignore m for manual boot and s to stop mounting..

Please suggest to remove this error.

---

### Post by oldfred on 2014-04-24
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

trusty version does not exist yet.
      
  ----------- WORKAROUND 0 sandyd  complied it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)

---

### Post by joshisapan on 2014-11-03
Thanks.. the error is removed. May be the image was not downloaded correctly. I again downloaded the image for ubuntu 14.04 and now both the operating system are running smoothly that is windows 7 ultimate and ubuntu 14.04. Thanks once again for the help

---

