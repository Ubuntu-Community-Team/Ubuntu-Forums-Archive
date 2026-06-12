---
title: "Invalid MBR Signature found."
date: 2015-07-01
forum: Installation &amp; Upgrades
---

### Post by luis67 on 2015-07-01
Hi! everyone I need your help!


The electricity had been interrupted while i was copying a VM, and when I tried to reboot the server didn't booted 

this appear on the screen 

```
[COLOR=#000000]*mount: mounting /dev on /root/dev failed: no such file or directory*[/COLOR]
[COLOR=#000000]*mount: mounting /sys on /root/sys failed: no such file or directory*[/COLOR]
[COLOR=#000000]*mount: mounting /proc on /root/proc failed: no such file or directory*[/COLOR]
[COLOR=#000000]*Target filesystem doesn't have /sbin/init.*[/COLOR]
[COLOR=#000000]*No init fount. Try passing init= bootarg.*[/COLOR]
[COLOR=#000000]*BusyBox v1.21.1(Ubuntu 1:1.21.0 - 1ubuntu1)built-in shell*[/COLOR]
[COLOR=#000000]*enter 'help' for a list of built-in commands*[/COLOR]
[COLOR=#000000]*(initframs).*[/COLOR]
```

I tried with slax to see what was going on and
then I got this

```

                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => No known boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 500480 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /slax/boot/ 
                       directory. No errors found in the Boot Parameter Block.
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


Invalid MBR Signature found.




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 15.6 GB, 15610576896 bytes
255 heads, 63 sectors/track, 1897 cylinders, total 30489408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *              2    30,489,407    30,489,406   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0       bd8b229c-df6e-4bd8-902d-7e72c07095b1   ext2       
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/sdb1        16EC-A9CE                              vfat       SIN TITULO
/dev/zram0       7638628b-f686-41e7-9f88-ad9ee67ac294   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options






======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown MBR on /dev/sda






=============================== StdErr Messages: ===============================


hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
  /dev/sda: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda: read failed after 0 of 4096 at 1000204795904: Input/output error
  /dev/sda: read failed after 0 of 4096 at 1000204877824: Input/output error
  /dev/sda: read failed after 0 of 4096 at 4096: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 991721095168: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 991721152512: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 4096: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 8480817152: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 8480874496: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 4096: Input/output error
  No volume groups found
mdadm: No arrays found in config file or automatically




```

I tried with fsck but anithing, I got
[B]
fsck: could this be a zero-length partition?
[/B]Please Help me!

---

### Post by oldfred on 2015-07-01
MBR shows no valid boot code, nor any partition table. Or similar to a blank drive.

Since no partitions you cannot run any partition repairs.

I might try testdisk. It may find old partitions, but any power failure during a major partition change usually corrupts partition and may not recoverable except from backup.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

    
Do not know of slax can run testdisk or has it. Better to have live installer with current version of Ubuntu for repairs.

---

### Post by luis67 on 2015-07-01
Ok I'll try with testdik 

but  why I can't see my sdba disk?

---

### Post by ubfan1 on 2015-07-01
If you know, down to the sector, your original partition starts and ends, (like you wrote them down, or you created them in an easily remembered way), try just recreating the partition table (use fdisk, or gdisk, or ...)  with those values instead of having a program like testdisk guess them.  You still may have problems, but then things like fsck should be of some help.

---

### Post by luis67 on 2015-07-07
Well after all my HDD died, apparently I was using a Repaired Disk of Segagate and the power failure killed it 

Before that I had tried to repair my boot and my MBR  I give you the result of boot-repair
[http://paste.ubuntu.com/11831246/](http://paste.ubuntu.com/11831246/)

---

