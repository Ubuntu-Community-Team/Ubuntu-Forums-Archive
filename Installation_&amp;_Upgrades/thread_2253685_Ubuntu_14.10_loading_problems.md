---
title: "Ubuntu 14.10 loading problems"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by redtail82 on 2014-11-21
I decided to update my Ubuntu 14.04 lts to Ubuntu 14.10 everything seem to work good I got an error about something about python so I went to reboot the system and try to figure something out well when I rebooted Ubuntu 14.10 is trying to install all I get it the loading screen nothing more I need help I can't lose all my data on the laptop I have urs of family pictures on here please help

---

### Post by redtail82 on 2014-11-21
Help I trued upgrading my Ubuntu now all I get it is Ubuntu 14.10 with the dots below it won't do nothing else help please I have years of family photos on this laptop

---

### Post by blnl on 2014-11-21
Before you start repairing Ubuntu, backup your personal files to an external drive, or a DVD.

Follow the steps as described below and you shall be fine:
1. download SystemRescueCd ISO image ([http://www.sysresccd.org/Download](http://www.sysresccd.org/Download))
2. burn this ISO image on a CD
3. boot you broken machine from the SystemRescueCd
4. start the terminal and type "blkid" to see the partitioning scheme of your HDD
5. create a directory to mount the partition from which you want to recover the files "mkdir /mnt/my_partition"
6. mount the partition "mount /dev/sda# /mnt/my_partition" (replace # with the proper partition number)
7. and there are your files "cd  /mnt/my_partition"

---

### Post by QIII on 2014-11-21
Threads merged.

Please do not start multiple threads about the same issue.  It dilutes the community's efforts to help and causes confusion by having different users attempt to provide support in two places.

Thanks.

---

