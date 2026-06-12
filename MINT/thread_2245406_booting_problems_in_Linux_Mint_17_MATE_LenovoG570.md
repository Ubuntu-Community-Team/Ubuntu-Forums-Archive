---
title: "booting problems in Linux Mint 17 MATE_LenovoG570"
date: 2014-09-23
forum: MINT
---

### Post by iokara08 on 2014-09-23
Good evening,

2 weeks ago I installed linux mint 17 MATE Edition 64 bit on a Lenovo G570 of a friend. As she told me everything was just perfect until today when she couldn't boot in the desktop environment. I am using Ubuntu or Mint, for several years and I had never experienced the following issue which also constitutes our problem:

''Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay=(did the system wait long enough?)
-Missing Modules (cat /proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/3e3ca5d7-3ed6-45a2-a74f-29aebe30c5db does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_ ''

I searched on the internet for a while and I followed the instructions of the following solution:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

I wotked on the terminal and it showed me that the superblock was modified but still I get the same problem.

Is it possible that my HDD is problematic or it is just a boot issue?

Tjhank you in advance for your time and solutions

---

### Post by slickymaster on 2014-09-23
*Moved to the ***Other Operating Systems and Projects*** sub-forum*

---

### Post by iokara08 on 2014-09-23
Good evening again,

Is it possible that this issue occured because of a damaged HDD? As she told me she changed recently laptop's default HDD with an old one because the first was damaged. I will try to format again and see if the HDD will be able to accept the installation files.

What do you think about it?

---

### Post by Mrnumber3isme on 2014-09-23
I wish you the best of luck, iokara. I'm experiencing the same issue. maybe the steps I've taken can help you. Here's a link to my thread on this topic
[http://ubuntuforums.org/showthread.php?t=2245163](http://ubuntuforums.org/showthread.php?t=2245163)

---

### Post by tgalati4 on 2014-09-23
> ALERT! /dev/disk/by-uuid/3e3ca5d7-3ed6-45a2-a74f-29aebe30c5db does not exist. Dropping to a shell!

This line is consistent with a drive that has failed completely OR the drive was swapped and the GRUB2 configuration was not updated with the UUID of the new-old disk.

Some reading:

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

