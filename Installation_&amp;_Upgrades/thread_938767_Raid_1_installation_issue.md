---
title: "Raid 1 installation issue"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by amitmo on 2008-10-05
have installed ubuntu 8.04 on the desktop.

i have configured raid 1 on the disk.

following is the details
ammo@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      195310080 blocks [2/2] [UU]


The issue is i a not able to write to md0


Any help will be appreciated...........

---

### Post by lemming465 on 2008-10-11
I'm confused by where the "desktop" is.  How many disks are there, and how many partitions?  Output from "sudo fdisk -l; mount; df -m" would help.  If you have two disks, made a single raid partition, and installed ubuntu to that, then your root partition is probably mounted from /dev/md0 already.  If your root filesystem is somewhere else, and you want to use extra space on /dev/md0 for something, then it would have to be formatted with a filesystem and mounted somewhere.

When you say you can't write to md0, what command are you running, and what error message are you getting?

---

