---
title: "Partition help"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by andjustmaybe on 2010-01-27
Ok, well let me start by saying this. Currently i have Ubuntu and windows 7 on my laptop duel booted. A couple of days ago i was trying to install a third os (another linux os) and i chose to use largest amount of continuous free space that i had made and it decided that my win 7 partition counted as free space. So i used my recov disks to reinstall win 7 and got it working and did some updates. Then i started my computer and it came up and said "Grub loading..." then shut down and restarted and kept doing this over and over again. What i want to do now is completely get rid of my windows and linux partitions. Currently i am booted into ubuntu from disc. I am just wondering 1) If there is any other way to either make grub work right or get rid of grub for now. and 2) what partitions should i delete? is grub on its own partition or part of the ubuntu partition?
I know this is a lot to comprehend but thanx for any help it is much appreciated!
Btw if it matters all my os's are 64-bit

---

### Post by kansasnoob on 2010-01-27
Well let's see what you really have. Please post the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Sef on 2010-01-27
what version of ubuntu do you have?

How did you install it? clean or upgrade?

---

### Post by andjustmaybe on 2010-01-27
```

```============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4e074e07

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,788,295   625,137,344   600,349,050   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        5AC8179EC8177789                       ntfs       SYSTEM RESERVED               
/dev/sda3        0AABAB8C1734505D                       ntfs       Gateway                       

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

aufs             /                aufs       (rw)
/dev/sr0         /cdrom           iso9660    (rw)
/dev/loop0       /rofs            squashfs   (rw)
```

```

i have ubuntu version 9.10

---

### Post by andjustmaybe on 2010-01-27
I deleted the ubuntu partitions and reformated them. I had ubuntu 9.10. At this point my main concern is removing grub  because it was not removed when i deleted my ubuntu partitions...

---

### Post by raymondh on 2010-01-27
> **andjustmaybe said:**
>  At this point my main concern is removing grub  because it was not removed when i deleted my ubuntu partitions...


GRUB is installed in the MBR of a HD.  To return to original config using the win7 bootloader, you'll need to restore that.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Raymond

---

### Post by andjustmaybe on 2010-01-28
Ok well that presents another problem in itself. I did not get an actual win 7 recov disk. I made recovery disks from the computer when i got it but these disks do not have the option to open command promt... Is there any way i can do the equivalent of thise from ubuntu? or anything else i can do?

---

### Post by andjustmaybe on 2010-01-28
Thanks for the feedback everyone. I downloaded a disc that had the recovery tools on it and got everything working again.

---

### Post by raymondh on 2010-01-28
glad to hear.  Happy ubuntu-ing.

---

