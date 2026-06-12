---
title: "Ubuntu installation made Windows disappear"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by Dr Spliff on 2011-10-04
I have searched endlessly on Google and tried multiple fixes for this, and nothing seems to be working.



What I'm trying to do :

-Triple boot (future Quad) Windows 7, XP, and Ubuntu



What I did:

-Had W7 Installed originally

-Executed GParted to Partition my drive the following way :

  *200 GB W7 (Primary)

  *100 GB Unallocated

-Inserted XP and installed on 100 GB partition

-Inserted Ubuntu and used drive partitioner on install to set the now XP 100 GB to 50 GB, and 50 GB set for Ubuntu



Everything was going OK, until I restarted and the GRUB2 Menu did not display my XP.  I have read up on editing the GRUB2 and executed on all sda options to no avail.  It listed Windows 7 Loader, which actually loaded XP....and W7 would not load at all.  After trying countless things with the GRUB2 menu, I resorted to a tip I found.  I inserted the W7 install CD and ran startup repair, which then made W7 boot from the W7 Loader option.  

I now cannot find, or boot XP.  I have tried custom adding it to GRUB2, but it does not find it ever.  Here is the hard drive analysis :


```
sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   421,412,863   421,206,016   7 NTFS / exFAT / HPFS
/dev/sda3         421,417,141   625,141,759   203,724,619   f W95 Extended (LBA)
/dev/sda5         421,417,143   523,268,705   101,851,563   7 NTFS / exFAT / HPFS
/dev/sda6         523,270,144   625,141,759   101,871,616  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        084A63AC4A63956A                       ntfs       
/dev/sda2        04366815366809CE                       ntfs       
/dev/sda5        888019FB8019F104                       ntfs       
/dev/sda6        5279cc91-5d11-44cc-b163-0f7c35c6f622   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

```

If I try to boot SDA5 it switches to a screen with a blinking cursor in the upper left corner, and just sits there.  How do I boot XP?  Thanks...

---

### Post by Dr Spliff on 2011-10-04
Sixty six people are stumped by this?

---

### Post by 4llf0rn0t on 2011-10-04
Hi,

Try editing your windows 7 boot menu with bcdedit.  It might have changed when you repaired it.

As pjd99 suggested, the entry for Windows XP may have been removed from your BCD store and you need to add it back.

---

### Post by pjd99 on 2011-10-04
Looking at the partition info, sda5 has nothing for the "boot files" line. 
Win 7 calls: /Windows/System32/winload.exe

Is this a problem?

Can you add the XP partition to the Windows boot loader in Win7? I think you can edit boot options with msconfig. Won't help with grub, but should allow you to see if the XP partition can boot.

---

### Post by oldfred on 2011-10-05
It is best not to install any windows in a logical partition, but it works.

Windows combines all its boots into the active partition (boot flag). It litterally moves all the boot files from a second install to the active partition. Grub then cannot find any boot files in your XP install as it has none and can only be booted from the Windows 7 active partition.

Examples are mostly Vista, but Windows 7 is the same except most installs of Windows 7 have a hidden 100MB boot/recovery partition.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

