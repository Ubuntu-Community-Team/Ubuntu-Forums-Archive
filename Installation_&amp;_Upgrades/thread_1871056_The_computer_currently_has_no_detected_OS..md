---
title: "The computer currently has no detected OS."
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Sorebas on 2011-10-28
Hello, I am a newbe in here.
and i am not a native speaker, so my english is really poor.
so I hope you can understand it.

I have installed windows7 in my computer,
when I try to install ubuntu,
it says The computer currently has no detected OS.
and I can't find any problem in my way.
so I hope I can get some helps in here.

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   390,703,103   390,496,256   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4C6E2D566E2D3A5A                       ntfs       &#49884;&#49828;&#53596; &#50696;&#50557;
/dev/sda2        70E83214E831D954                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/&#49884;&#49828;&#53596; &#50696;&#50557;  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/70E83214E831D954  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
```





This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.

Disk /dev/sda: 243201 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     12-     13-    102400    7  HPFS/NTFS
/dev/sda2         12+  24320-  24308- 195248128    7  HPFS/NTFS
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
Input in the following format; absent fields get a default value.
<start> <size> <type [E,S,L,X,hex]> <bootable [-,*]> <c,h,s> <c,h,s>
Usually you only need to specify <start> and <size> (and perhaps <type>).

---

### Post by Rubi1200 on 2011-10-28
Hi and welcome to the forums :)

It is likely that this is the problem:
> GUID Partition Table detected, but does not seem to be used.The only way I know to deal with this is using a tool written by a very experienced member:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Make sure you have backups before using it!

---

### Post by Sorebas on 2011-10-28
sorry,
but when i type [FONT=monospace]
[/FONT]**sudo fixparts /dev/sda1** it says
sudo: fixparts: command not found.

---

### Post by Rubi1200 on 2011-10-28
You could try downloading and running the version for WIndows; it is the zip file on the download page.
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.0/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.0/fixparts-binaries/)

---

