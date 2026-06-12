---
title: "[SOLVED] Gutsy 64bit grub problem (error 15)"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by spoddles on 2007-11-30
Greetings,

I have a grub problem that is resisting my efforts to resolve. Hoping someone out there has some ideas as I'm getting frustrated :confused:

_Historical_

[LIST=1]
[*]Upgraded from Feisty to Gutsy a while back
[*]64bit Gutsy was fully patched and working fine yesterday
[*]Rebooted last night into my gaming (XP) partition...no probs
[*]Rebooted again to try and load the Gutsy partition and am getting a grub error 15 (file not found)
[*]Thus far all actions taken to fix the problem haven't changed the error
[/LIST]

_Actions taken so far_

*All of these actions taken after booting the 64bit live CD*

[LIST=1]
[*]An fsck -Vfr of the root partition came up clean as a whistle
[*]Mounted my root partition plus /proc and /dev and chrooted
[*][COLOR="Red"]Found a very weirdly named zero length file in /boot/grub - I confess I deleted it before taking a record of the filename, but it did start with ??? and was 20-30 chars in length[/COLOR]
[*]Ran my standard grub-install (no errors reported)
[*]Windows doesn't appear to have monkeyed with the partition IDs as it sometimes will
[*]No changes have been made to the bios HDD ordering - mm to clarify I haven't made any changes, but will go and double check once I've posted this message (from the live CD) and will post a second message with my results
[*]Ran a binary compare of the grub stage files in /boot/grub with those in /usr/lib/grub/x86_64-pc - no difference found
[/LIST]
_Diagnostic info_

[INDENT]*Partition information*[/INDENT]

[INDENT]
Partition summary:
[LIST=1]
[*]sda = windows xp (and grub boot disk)
[*]sdb = bulk data
[*]sdc1 = linux root
[*]sdd = bulk data
[/LIST][/INDENT]

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00044930

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ead9ead

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033ee9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8666    69609613+  83  Linux
/dev/sdc2            8667        9039     2996122+   5  Extended
/dev/sdc5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90fe90fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19457   156288321   83  Linux

```

[INDENT]*Acquisition of root filesystem*[/INDENT]

```
root@ubuntu:~# mount /dev/sdc1 /mnt
root@ubuntu:~# mount -t proc none /mnt/proc
root@ubuntu:~# mount -o bind /dev /mnt/dev
root@ubuntu:~# cd /mnt
root@ubuntu:/mnt# chroot /mnt

```

[INDENT]*Reinstall grub (after acquiring root filesystem)*[/INDENT]
[INDENT]*[COLOR="Red"]no change to boot problem[/COLOR]*[/INDENT]
```

root@ubuntu:/# grub-install hd0
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd

```

[INDENT]*Contents of menu.lst*[/INDENT]

```
root@ubuntu:/boot/grub# egrep -v '^#|^$' menu.lst
default         0
timeout         10
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro quiet
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=88f59912-da00-413e-98ce-d387f05e7390 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
title           Ubuntu 7.10, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet
title           Other operating systems:
root
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1

```

[INDENT]*Files under /boot/grub (root partition)*[/INDENT]

```
root@ubuntu:/mnt/boot/grub# ls -l
total 204
-rw-r--r-- 1 root root    197 2007-11-30 12:22 default
-rw-r--r-- 1 root root     60 2007-10-21 12:52 device.map
-rw-r--r-- 1 root root   8660 2007-11-30 12:22 e2fs_stage1_5
-rw-r--r-- 1 root root   8452 2007-11-30 12:22 fat_stage1_5
-rw-r--r-- 1 root root     15 2007-11-30 12:22 installed-version
-rw-r--r-- 1 root root   9152 2007-11-30 12:22 jfs_stage1_5
-rw-r--r-- 1 root root   4558 2007-11-30 11:11 menu.lst
-rw-r--r-- 1 root root   7860 2007-11-30 12:22 minix_stage1_5
-rw-r--r-- 1 root root  10132 2007-11-30 12:22 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2007-11-30 12:22 stage1
-rw-r--r-- 1 root root 110292 2007-11-30 12:22 stage2
-rw-r--r-- 1 root root   9980 2007-11-30 12:22 xfs_stage1_5

```

[INDENT]*Filesystem check for root partition*[/INDENT]

```
root@ubuntu:/boot/grub# exit
root@ubuntu:/mnt# cd
root@ubuntu:~# umount /mnt/dev
root@ubuntu:~# umount /mnt/proc
root@ubuntu:~# umount /mnt
root@ubuntu:~# fsck -Vfr /dev/sdc1
fsck 1.40.2 (12-Jul-2007)
[/sbin/fsck.ext3 (1) -- /dev/sdc1] fsck.ext3 -fr /dev/sdc1 
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdc1: 144382/8716288 files (2.3% non-contiguous), 11946626/17402403 blocks
root@ubuntu:~# echo $?
0

```

[INDENT]*Contents of fstab*[/INDENT]

```
root@ubuntu:/mnt# cat etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
##########################################################################################################
# 64 bit root and swap
#

# /dev/sdc1
UUID=88f59912-da00-413e-98ce-d387f05e7390 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sdc5
UUID=51105e63-541e-4664-b44c-25e47b24cff9 none            swap    sw              0       0


##########################################################################################################
# Various media
#
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

##########################################################################################################
# Bulk storage
#

#/dev/sdb1
UUID=be162e8c-9c1a-4b54-96f0-30d9bf85049a /home/tony/Desktop/Data/video2 auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

#/dev/sdd1
UUID=d5c1e5ae-b8b5-4783-9615-3711912fcac7 /home/tony/Desktop/Data/video1 auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0

##########################################################################################################
# Other operating systems
#

# /dev/sda1
/dev/sda1 /windows/xp ntfs-3g defaults,locale=en_GB.UTF-8 0 0


```

[INDENT]*Manual grub installation (after chroot)*[/INDENT]

```
root@ubuntu:/boot/grub# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,0)
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit

```

---

### Post by spoddles on 2007-11-30
[SIZE="5"]Aaaaaarrrgghhhhh WINDOWS BITES THE MONKEY AGAIN!!![/SIZE]

Many apologies for any time you may have spent reading the previous post...

Windows, in all its wisdom, reached down into my bloody bios and reordered the damn HDDs!

Ye gods I hate windows.

The case is solved :mad:

---

