---
title: "Wont find my HDD when installing? O.o"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by RobertVincent on 2010-11-23
hi guys, i have a problem with my ubuntu...

when i try to install it via live CD it wont find my HDD and skips to the partition page, where nothing is displayed...

any ideas?

i tried installing it straight away, and from the testing part too.

---

### Post by lmarmisa on 2010-11-23
Welcome to the Ubuntu forums.

Start your system from the Live CD (option Try Ubuntu), open a terminal (Applications -> Accessories -> Terminal) and type this command:

```

sudo fdisk -l

```Please, post the output of this command.

---

### Post by RobertVincent on 2010-11-24
this is the outcome:

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track




is says no root file system when i get to the page to find/partition my HDD. cheers.

---

### Post by RobertVincent on 2010-11-24
any ideas people?

---

### Post by matt_symes on 2010-11-24
Hi

> ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'It's a small L and not the number one.

Try reposting the results.

Kind regards

---

### Post by RobertVincent on 2010-11-24
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd2c32a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20023   160731136    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

thats the outcome, what does it mean? cheers.

---

### Post by RobertVincent on 2010-11-24
[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]it says "No root file system is defined" when allocating..

it jumped straight from the Preparing to install screen to the allocate drive screen aswel... if that helps fix the problem?..

---

### Post by lmarmisa on 2010-11-24
Your 167 Gbytes hard drive is detected by the Ubuntu Live CD as expected.

The image of your previous post is broken. Please, postit again.

I would like to know if you try to install a dual boot system or a [Wubi]("https://wiki.ubuntu.com/WubiGuide") Ubuntu system.

---

