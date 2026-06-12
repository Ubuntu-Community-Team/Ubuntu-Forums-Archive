---
title: "remove old kernels through Boot-Repair"
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by kuv02 on 2015-11-28
Hi,

I have a problem with "[COLOR=#000000][FONT=Trebuchet MS]kernel panic-not syncing: VFS: unable to mount root fs on unknown block(0,0)" and could trace it down (through [this]("http://www.ubuntu-forum.de/artikel/65502/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block-0-0.html") [threads]("http://ubuntuforums.org/showthread.php?t=2302981")) to a full boot partition.

I was told to use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to check my system. Boot-Repair is currently the only way I can access my system (I also have a Fedora Live DVD around, but never used it)

I tried to remove old kernels as described in [this ubuntu-help Article]("https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels"). 
But this does not work, because the article assumes I'm in the system whose kernels I want to clean up. But I am in Boot-Repair. I have no clue how to access the kernels and clean them.

From the [boot-repair report]("http://paste.ubuntu.com/13441685/") i could see, that I need to mount drives etc. I really would need help with this. I try to fix this problem for 3 weeks.
[/FONT][/COLOR]

---

### Post by kuv02 on 2015-11-28
This is the content of my boot partition. What shall I delete and How do I do this?
```
lubuntu@lubuntu:/$ sudo mount -t ext2 /dev/sda1 /mnt/boot-sav/sda1lubuntu@lubuntu:/$ cd /mnt/boot-sav/sda1/
lubuntu@lubuntu:/mnt/boot-sav/sda1$ ls -lp
total 220566
-rw-r--r-- 1 root root  1268815 Apr 17  2015 abi-3.19.0-15-generic
-rw-r--r-- 1 root root  1269284 Mai 19  2015 abi-3.19.0-18-generic
-rw-r--r-- 1 root root  1269462 Mai 29  2015 abi-3.19.0-20-generic
-rw-r--r-- 1 root root  1269462 Jun 14 19:44 abi-3.19.0-21-generic
-rw-r--r-- 1 root root  1270417 Jul 24 23:35 abi-3.19.0-25-generic
-rw-r--r-- 1 root root  1271689 Okt 21 11:54 abi-3.19.0-32-generic
-rw-r--r-- 1 root root   177656 Apr 17  2015 config-3.19.0-15-generic
-rw-r--r-- 1 root root   177700 Mai 19  2015 config-3.19.0-18-generic
-rw-r--r-- 1 root root   177700 Mai 29  2015 config-3.19.0-20-generic
-rw-r--r-- 1 root root   177700 Jun 14 19:44 config-3.19.0-21-generic
-rw-r--r-- 1 root root   177771 Jul 24 23:35 config-3.19.0-25-generic
-rw-r--r-- 1 root root   177782 Okt 21 11:54 config-3.19.0-32-generic
drwxr-xr-x 5 root root     1024 Nov 11 15:41 grub/
-rw-r--r-- 1 root root 30861158 Mai 25  2015 initrd.img-3.19.0-15-generic
-rw-r--r-- 1 root root 30864964 Jun 14 14:45 initrd.img-3.19.0-18-generic
-rw-r--r-- 1 root root 30865915 Jun 14 14:47 initrd.img-3.19.0-20-generic
-rw-r--r-- 1 root root 30865311 Jun 17 19:15 initrd.img-3.19.0-21-generic
-rw-r--r-- 1 root root 30872082 Jul 31 19:56 initrd.img-3.19.0-25-generic
drwx------ 2 root root    12288 Mai 23  2015 lost+found/
-rw-r--r-- 1 root root   164216 Mär  6  2015 memtest86+.bin
-rw-r--r-- 1 root root   165892 Mär  6  2015 memtest86+.elf
-rw-r--r-- 1 root root   166396 Mär  6  2015 memtest86+_multiboot.bin
-rw------- 1 root root  3615358 Apr 17  2015 System.map-3.19.0-15-generic
-rw------- 1 root root  3616263 Mai 19  2015 System.map-3.19.0-18-generic
-rw------- 1 root root  3617303 Mai 29  2015 System.map-3.19.0-20-generic
-rw------- 1 root root  3617303 Jun 14 19:44 System.map-3.19.0-21-generic
-rw------- 1 root root  3617653 Jul 24 23:35 System.map-3.19.0-25-generic
-rw------- 1 root root  3622220 Okt 21 11:54 System.map-3.19.0-32-generic
-rw-r--r-- 1 root root  6611584 Mai 23  2015 vmlinuz-3.19.0-15-generic
-rw------- 1 root root  6614144 Mai 19  2015 vmlinuz-3.19.0-18-generic
-rw------- 1 root root  6616960 Mai 29  2015 vmlinuz-3.19.0-20-generic
-rw------- 1 root root  6617408 Jun 14 19:44 vmlinuz-3.19.0-21-generic
-rw------- 1 root root  6616704 Jul 24 23:35 vmlinuz-3.19.0-25-generic
-rw------- 1 root root  6623936 Okt 21 11:54 vmlinuz-3.19.0-32-generic



```[COLOR=#34A042][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-11-28
Delete any of the 3.19.0-15 files. Those are the oldest.
BUT also replace them with empty files of *exactly *the same name. The 'touch' command is handy for that.

Those files are placed by the package manager, and must be removed by the package manager; if you simply delete them, you exchange a broken system for a differently-broken system. 
The trick here is that the package manager doesn't care at all about the *contents* or *size* of the file.

Once your system is bootable, remove those old kernels using the package manager.

---

### Post by grahammechanical on 2015-11-28
If you are getting a Grub boot menu you can go into Advanced Options for Ubuntu and select recovery mode. the recovery menu will give, amongst others, these options

> Clean  try to make free space
Root drop to a root shell prompt

The file system will be in read only mode. To put it in read/write mode run one of the other options such as Network and then use the root shell prompt to purge kernels as decribed here.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

Typing Exit will bring you back to the recovery menu where Resume will try to load to a desktop.

Regards.

---

### Post by kuv02 on 2016-01-02
I was pointed out to the possability to boot into older kernels via grubs "Ubuntu advanced boot options". I than removed the unnecessary kernels via the package manager.

---

### Post by dmtparker on 2016-01-02
How do you get into "Ubuntu advanced boot options"? I need to boot into an older kernal (usb3 does not work under latest - see other post) but at least in my version of ubuntu studio (14.04.3) grub is silent and not interactive. I've tried all the usual keys (<shift> <cntrl> <alt> <esc>) to no avail.

---

