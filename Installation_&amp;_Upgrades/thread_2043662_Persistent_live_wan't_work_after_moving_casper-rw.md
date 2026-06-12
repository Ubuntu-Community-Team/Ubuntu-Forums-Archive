---
title: "Persistent live wan't work after moving casper-rw"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2012-08-17
Hi,
I want to use a 32GB USB memory as a live Ubuntu with persistence.
Initially, I tried from within Ubuntu (12.04-386), but it would boot.
Afterwards I used gparted to create 3 partitions on above USB memory: 
1 a bootable 3.8GB FAT32 partition labeled UBUNTU
2. 3.8 GB FAR32 partition labeled WINDOWS (for data exchange between OSs)
3. A large (rest of un allocated space) ext2 partition labeled casper-rw.

I used unetbootin to create a persistent Ubuntu (same version) on the UBUNTU partition.

I rebooted and verified the USB worked (I was able to boot into Ubuntu).

I rebooted back (into my Arch) and, as root, used "rsync-av" to move all the contents that has been in the casper-rw folder (in Ubuntu partition) to the otherwise entry large casper-rw partition. Afterwards I deleted to folder casper-rw (and its contents) from the Ubuntu partition.

Trying to reboot from the USB, I get the following error: "initrmfs unable to find media containing a live filesystem".

Below see a terminal out of the current structure and contents of my USB memory.

Please advise!

Thanks

--------USB structure-from terminal
```

# fdisk -l /dev/sdc

Disk /dev/sdc: 32.0 GB, 32007389184 bytes
64 heads, 32 sectors/track, 30524 cylinders, total 62514432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018802

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048     1775615      886784    b  W95 FAT32
/dev/sdc2         1775616     9558015     3891200    b  W95 FAT32
/dev/sdc3         9558016    62511103    26476544   83  Linux
[root@Miki_Arch Documents]# cd /media/
[root@Miki_Arch media]# ls -al
total 12
drwxr-xr-x  3 root root 4096 Aug 17 09:51 .
drwxr-xr-x 27 root root 4096 Aug 16 11:29 ..
drwxr-xr-x  2 root root 4096 Aug 17 09:45 casper-rw
[root@Miki_Arch media]# cd /media/casper-rw/
[root@Miki_Arch casper-rw]# ls -al
total 708372
drwxr-xr-x 2 root root       4096 Aug 17 09:45 .
drwxr-xr-x 3 root root       4096 Aug 17 09:51 ..
-rw-r--r-- 1 miki users     41315 Apr 23 15:27 filesystem.manifest
-rw-r--r-- 1 miki users      1079 Apr 23 15:27 filesystem.manifest-remove
-rw-r--r-- 1 miki users        11 Apr 23 15:27 filesystem.size
-rw-r--r-- 1 miki users 704692224 Apr 23 15:27 filesystem.squashfs
-rw-r--r-- 1 miki users  14873857 Apr 23 15:27 initrd.lz
-rw-r--r-- 1 miki users   5015840 Apr 23 15:27 vmlinuz


```

---

### Post by efflandt on 2012-08-18
You must have done something wrong.  Those files do not belong in casper-rw.  When I loop mount a casper-rw file on /media/vdisk:

```
efflandt@XPS8100-1204:/media/vdisk$ **ls -l**
total 68
drwxr-xr-x  3 root root  4096 Apr 25 11:10 boot
drwxr-xr-x  2 root root  4096 Jul  8 08:44 cdrom
drwxr-xr-x 13 root root  4096 Jul 21 20:49 etc
drwxr-xr-x  3 root root  4096 Jul  8 08:44 home
drwxr-xr-x  3 root root  4096 Apr 25 11:08 lib
drwx------  2 root root 16384 Jul  8 13:26 lost+found
drwxr-xr-x  2 root root  4096 Jul  8 19:09 media
drwxr-xr-x  4 root root  4096 Jul 21 20:38 mnt
drwxr-xr-x  2 root root  4096 Jul  8 08:44 rofs
drwx------  6 root root  4096 Jul  8 13:57 root
drwxr-xr-x  2 root root  4096 Jul  8 14:02 target
drwxrwxrwt  7 root root  4096 Jul 21 13:56 tmp
drwxr-xr-x  6 root root  4096 Apr 25 11:04 usr
drwxr-xr-x  7 root root  4096 Jul 21 20:49 var
```You apparently copied the files from the "casper" directory, instead of loop mounting "casper-rw" and copying the contents of that:

```
efflandt@XPS8100-1204:/media/vdisk$ **ls -l /media/EC19-C886/casper**
total 698876
-rw-r--r-- 1 efflandt efflandt     41031 Jul  8 08:19 filesystem.manifest
-rw-r--r-- 1 efflandt efflandt       971 Jul  8 08:19 filesystem.manifest-remove
-rw-r--r-- 1 efflandt efflandt        11 Jul  8 08:19 filesystem.size
-rw-r--r-- 1 efflandt efflandt 695623680 Jul  8 13:20 filesystem.squashfs
-rw-r--r-- 1 efflandt efflandt  14999791 Jul  8 13:20 initrd.lz
-rw-r--r-- 1 efflandt efflandt   4965840 Jul  8 08:20 vmlinuz
```

However, I have never figured out how to get live/install iso to use a separate partition labelled as "casper-rw", maybe because I did not know to copy the contents of a loop mounted casper-rw to it.

BTW ext2 would probably be better to use for flash memory (less writing than a journal file system).  And if you have 32 GB, why not just do a regular install to it, so you can do kernel updates, or if you need non-default video drivers?  To compare, I installed both 64-bit Lubuntu and Ubuntu 12.04 with common /home partition to 32 GB SD for my tablet PC.

---

