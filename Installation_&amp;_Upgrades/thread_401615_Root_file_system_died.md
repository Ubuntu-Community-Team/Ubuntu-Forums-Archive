---
title: "Root file system died"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by daftman on 2007-04-04
I've been using ubuntu for more than over 8 months now. I have been upgrading from dapper all the way to fiesty. However, after some upgrade last night, this morning I cannot boot into my system. It just hung on the ubuntu splash screen. The progress bar didn't move. My current kernel is linux-2.6.20-13 generic. I tried booting with another kernel linux-2.6.20-12-generic and the same thing happen. I can't even get a prompt. Upon trying the linux-2.6.20-11-generic the system boot and display some errors while doing 'fsck'. I got a commmand prompt and logged on to the system only to discover that my root partition is gone (or seem like it)
$>ls / 
display nothing
$>ls /bin
display nothing
I tried running fsck manually on my root partition /dev/sda1 but i get the error: 
fsck: fsck.ext2: not found
Error 2 while executing fsck.ext2 for /dev/sda1
I tried some the common commands most of them fail. E.g
whereis 
apt-get
dpkg-query
locate

I tried ls /dev/sda1 but it does not exist
I tried ls /dev/evms and it display sda1 sda2 sda3

Is there something wrong with evms? Is it not running?

Despite the error, my services such as mysql, apache2, ssh, samba are all running.

What can I do? How can I get my root partition back? Please help. This is very urgent as I cannot get into gnome or kubuntu to do work.

---

### Post by Feb29 on 2007-04-04
not too bad.
run fdisk -l to check your patitions and
try mount them to mountpoints.
at lease you have the opportunity to backup your data.

---

### Post by daftman on 2007-04-04
fdisk -l
"-bash: fdisk: command not found"

Some of the command does not work. I think fdisk is one of them

---

### Post by dreadlord_chris on 2007-04-05
> **daftman said:**
> fdisk -l
"-bash: fdisk: command not found"

Some of the command does not work. I think fdisk is one of them

Have you tried Recovery Mode? Also, booting into a LiveCD will give you access to fdisk

---

