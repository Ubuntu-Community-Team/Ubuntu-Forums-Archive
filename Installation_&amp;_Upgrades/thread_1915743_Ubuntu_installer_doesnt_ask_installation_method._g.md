---
title: "Ubuntu installer doesnt ask installation method. goes to empty partition box instead"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by XxTriviumxX on 2012-01-26
I want to install ubuntu alongside windows 7 but the live dvd installer doesnt let me choose any installation type (full disk, alongside windows, something else...) instead it goes directly to the partitioning step. and there, i cannot see any partitions. heres a screenshot :

[[IMG]http://img820.imageshack.us/img820/4221/screenshotat20120127003.png[/IMG]]("http://imageshack.us/photo/my-images/820/screenshotat20120127003.png/")

---

### Post by varunendra on 2012-01-27
Hi,

Please post output of:
```
sudo fidsk -l
```
(it's a small "*L*" after *fdisk*)

---

### Post by Mark Phelps on 2012-01-27
It's very likely your Win7-preinstalled PC already has the maximum of 4 primary partitions established on your hard drive.  And in that case, the Ubuntu installer can NOT install -- hence, no selections being offered,

The "fdisk" command will show the contents of your drive -- so we can advise you further.

---

### Post by XxTriviumxX on 2012-01-27
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69b9b67a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

---

### Post by darkod on 2012-01-27
This also happens if there is an error or corruption in the partition table. Windows often ignores them but linux doesn't.
Try running fixparts and see if it finds something:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by XxTriviumxX on 2012-01-27
> **darkod said:**
> This also happens if there is an error or corruption in the partition table. Windows often ignores them but linux doesn't.
Try running fixparts and see if it finds something:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)



FixParts 0.8.0

Loading MBR data from /dev/sda

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0x69B9B67A
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048       206847   primary     Y        Y      0x07
   2                206848   1953521663   primary              Y      0x07

MBR command (? for help): ^                
a    toggle the active/boot flag
c    recompute all CHS values
l    set partition as logical
o    omit partition
p    print the MBR partition table
q    quit without saving changes
r    set partition as primary
s    sort MBR partitions
t    change partition type code
w    write the MBR partition table to disk and exit

---

### Post by Quackers on 2012-01-27
You can either press W and write the partition table to disc (which looks ok - but just as it appeared before) or press q to quit and exit.

The output of ```
sudo fdisk -lu
``` may show up something.

Have you changed any partitions lately?
Are you using RAID?

Actually, looking at your screenshot the installer is not finding your drive (not just the partitions).
Are you using SATA3 ports?

---

### Post by XxTriviumxX on 2012-01-27
> **Quackers said:**
> You can either press W and write the partition table to disc (which looks ok - but just as it appeared before) or press q to quit and exit.

The output of ```
sudo fdisk -lu
``` may show up something.

Have you changed any partitions lately?
Are you using RAID?

Actually, looking at your screenshot the installer is not finding your drive (not just the partitions).
Are you using SATA3 ports?

i was using raid.. switched to ahci 

ive re installed windows 7 ...because i thought the original windows 7 by acer was the problem then another time because of ahci..i dont know about sata3 ports i will check on that ...ill do that output too

---

### Post by darkod on 2012-01-27
If you used the disk in raid it has meta data left. Windows ignores it, but again, ubuntu doesn't.

If you ARE NOT running raid any more, boot with the ubuntu cd in live mode and in terminal:
sudo dmraid -E -r /dev/sda

Then start the install process.

---

### Post by XxTriviumxX on 2012-01-27
omfg thanks man!!!

---

### Post by darkod on 2012-01-27
No problem. Enjoy it. :)

---

