---
title: "Boot error trying to boot from a persistent USB memory"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2012-08-15
Hi,
I booted from the Ubuntu 12.04-386 CD and chose to prepare a bootable USB, with a 3.9GB persistent file on a 32GB USB memory.
Ubuntu claimed to complete the procedure successfully, yet, when trying to boot from that USB memory (I've checked both as USB-HDD and USB-CD available in my BIOS), I get a "boot error". 
The USB memory itself worked fine till yesterday (on the same PC), acting as a live Linux Mint.

Enclosed please find respective terminal output (ran on my Arch system).
Please advise !

Thanks!

-------copy of Arch terminal--------------
```

# fdisk -l
....


Disk /dev/sdc: 32.0 GB, 32007389184 bytes
64 heads, 32 sectors/track, 30524 cylinders, total 62514432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cf440

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    62513151    31256560    c  W95 FAT32 (LBA)
[root@Miki_Arch Documents]# cd /media/
[root@Miki_Arch media]# ls
82B6-EFC7
[root@Miki_Arch media]# cd 82B6-EFC7/
[root@Miki_Arch 82B6-EFC7]# ls -al
total 4132484
drwx------ 11 miki users      16384 Jan  1  1970 .
drwxr-xr-x  3 root root        4096 Aug 15 12:36 ..
drwx------  2 miki users      16384 Aug 15 09:14 .disk
-rw-r--r--  1 miki users        231 Aug 15 09:14 README.diskdefines
-rw-r--r--  1 miki users        134 Aug 15 09:14 autorun.inf
drwx------  3 miki users      16384 Aug 15 09:14 boot
drwx------  2 miki users      16384 Aug 15 09:16 casper
-rw-r--r--  1 miki users 4228907008 Aug 15 09:29 casper-rw
drwx------  3 miki users      16384 Aug 15 09:16 dists
drwx------  2 miki users      16384 Aug 15 09:16 install
-r--r--r--  1 miki users      32256 Aug 15 09:17 ldlinux.sys
-rw-r--r--  1 miki users       4237 Aug 15 09:14 md5sum.txt
drwx------  2 miki users      16384 Aug 15 09:17 pics
drwx------  4 miki users      16384 Aug 15 09:17 pool
drwx------  2 miki users      16384 Aug 15 09:17 preseed
drwx------  2 miki users      16384 Aug 15 09:17 syslinux
-rwxr-xr-x  1 miki users    2502608 Aug 15 09:14 wubi.exe


```

---

### Post by mibadt on 2012-08-15
Some additional info from my ternial...

Thanks

-----------copy of terminal----------
```

# cd 82B6-EFC7/

[root@Miki_Arch 82B6-EFC7]# ls -al
total 4132484
drwx------ 11 miki users      16384 Jan  1  1970 .
drwxr-xr-x  3 root root        4096 Aug 15 12:36 ..
drwx------  2 miki users      16384 Aug 15 09:14 .disk                                                                                                                      
-rw-r--r--  1 miki users        231 Aug 15 09:14 README.diskdefines                                                                                                         
-rw-r--r--  1 miki users        134 Aug 15 09:14 autorun.inf                                                                                                                
drwx------  3 miki users      16384 Aug 15 09:14 boot                                                                                                                       
drwx------  2 miki users      16384 Aug 15 09:16 casper
-rw-r--r--  1 miki users 4228907008 Aug 15 09:29 casper-rw
drwx------  3 miki users      16384 Aug 15 09:16 dists
drwx------  2 miki users      16384 Aug 15 09:16 install
-r--r--r--  1 miki users      32256 Aug 15 09:17 ldlinux.sys
-rw-r--r--  1 miki users       4237 Aug 15 09:14 md5sum.txt
drwx------  2 miki users      16384 Aug 15 09:17 pics
drwx------  4 miki users      16384 Aug 15 09:17 pool
drwx------  2 miki users      16384 Aug 15 09:17 preseed
drwx------  2 miki users      16384 Aug 15 09:17 syslinux
-rwxr-xr-x  1 miki users    2502608 Aug 15 09:14 wubi.exe


[root@Miki_Arch 82B6-EFC7]# cd boot/
[root@Miki_Arch boot]# ls -al
total 48
drwx------  3 miki users 16384 Aug 15 09:14 .
drwx------ 11 miki users 16384 Jan  1  1970 ..
drwx------  2 miki users 16384 Aug 15 09:14 grub
[root@Miki_Arch boot]# cd grub/
[root@Miki_Arch grub]#  ls -al
total 48
drwx------ 2 miki users 16384 Aug 15 09:14 .
drwx------ 3 miki users 16384 Aug 15 09:14 ..
-rw-r--r-- 1 miki users   589 Aug 15 09:14 loopback.cfg
[root@Miki_Arch grub]# cd ..
[root@Miki_Arch boot]# cd ..
[root@Miki_Arch 82B6-EFC7]# cd casper/
[root@Miki_Arch casper]#  ls -al
total 707728
drwx------  2 miki users     16384 Aug 15 09:16 .
drwx------ 11 miki users     16384 Jan  1  1970 ..
-rw-r--r--  1 miki users     41315 Aug 15 09:14 filesystem.manifest
-rw-r--r--  1 miki users      1079 Aug 15 09:14 filesystem.manifest-remove
-rw-r--r--  1 miki users        11 Aug 15 09:14 filesystem.size
-rw-r--r--  1 miki users 704692224 Aug 15 09:16 filesystem.squashfs
-rw-r--r--  1 miki users  14873857 Aug 15 09:16 initrd.lz
-rw-r--r--  1 miki users   5015840 Aug 15 09:16 vmlinuz
[root@Miki_Arch casper]# 

```

---

