---
title: "Grub2 Upgrade Bug; &quot;symbol 'grub_term_highlight_color' not found&quot;"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by cathect2 on 2014-04-19
I have been bitten by [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977"), where upgrade from 13.10 to 14.04 breaks grub and gives the message "symbol 'grub_term_highlight_color' not found."

I have tried to chroot with a live cd to reload Grub, but am experiencing errors. Can someone suggest something? Here is my terminal printout:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000243e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   625141759   312569856   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d0df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       958269440   976773167     9251864   82  Linux swap / Solaris
/dev/sdb2   *        2048   958269439   479133696   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1050 MB, 1050935296 bytes
2 heads, 63 sectors/track, 16290 cylinders, total 2052608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046364

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     2052607     1026288    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mkdir -p /media/ubuntu
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /media/ubuntu
ubuntu@ubuntu:~$ sudo mount --bind /dev /media/ubuntu/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /media/ubuntu/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /media/ubuntu/sys
ubuntu@ubuntu:~$ sudo chroot /media/ubuntu
root@ubuntu:/# grub-install /dev/sdb2
Installing for i386-pc platform.
grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.
root@ubuntu:/# 

PS: I notice that grub is "installing for i386-pc" but I am running 64-bit. Is that an issue?

---

### Post by oldfred on 2014-04-19
You install grub to sdb not sdb2 as it is the boot loader in the MBR that you are installing.

I have seen one or two others with the i386-pc on 64 bit systems and that may be part of the error. Boot-Repair did report grub version issue which I have never seen before also.  I might suggest that you add those comments to the bug report.


You could try booting with SuperGrub and then running the sudo dpkg config commands from inside your install.
If that boots what does this say?
 grub-install -v

 
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)


 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by grahammechanical on 2014-04-19
I get "installing for i386-pc platform" when I run grub-update but it does not stop Grub being installed into the MBR and it does not cause any problems with booting. I don't worry about it.

---

### Post by Bashing-om on 2014-04-19
Et al,

I am still on 13.10, running AMD64 and I too recently encountered the i386-pc notification. (presently mystified what the function is in grub).
However for reference:
```

sysop@1310mini:~$ ls -la /boot/grub
total 2236
drwxr-xr-x 5 root root    4096 Apr 15 11:36 .
drwxr-xr-x 3 root root    4096 Apr 12 17:25 ..
drwxr-xr-x 2 root root    4096 May 19  2013 fonts
-rw-r--r-- 1 root root     699 Apr 12 17:22 gfxblacklist.txt
-r--r--r-- 1 root root    6740 Apr 15 11:36 grub.cfg
-r--r--r-- 1 root root   15427 Apr  6 09:39 grub.cfg~
-rw-r--r-- 1 root root    1024 Apr 19 19:54 grubenv
[color=blue]drwxr-xr-x 2 root root   12288 Apr 12 17:24 i386-pc[/color]
drwxr-xr-x 2 root root    4096 Apr 12 17:24 locale
-rw-r--r-- 1 root root 2226340 Apr 12 17:24 unicode.pf2
sysop@1310mini:~$ ls -la /boot/grub/i386-pc
total 2108
drwxr-xr-x 2 root root  12288 Apr 12 17:24 .
drwxr-xr-x 5 root root   4096 Apr 15 11:36 ..
-rw-r--r-- 1 root root   7456 Apr 12 17:24 915resolution.mod
-rw-r--r-- 1 root root  10024 Apr 12 17:24 acpi.mod
<snip>

and many many more .mod files.

```

Grub,
[INDENT][INDENT]it is achang'n
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-04-19
It used to be all the .mod files or loadable drivers were just in /boot/grub. But in newer installs /boot/grub has grub.cfg and several folders and all the .mod files are in that i386-pc. Not sure why that would be the naming convention.
But then some of the errors may be an old grub looking in the wrong file location for the loadable drivers or the new version not finding the folder? It would be needed if anything not standard had to be loaded to make grub boot install.

---

### Post by Bashing-om on 2014-04-19
@ oldfred, Thanks for that clarification.

[INDENT][INDENT]still learning
[INDENT][INDENT][INDENT]even after all these years
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Navneet_Kumar on 2014-04-20
i was also experiencing the same problem during my upgrade...but later i decided to freshly install 14.04 instead of upgrading and from there on everything works fine.....>:D

---

