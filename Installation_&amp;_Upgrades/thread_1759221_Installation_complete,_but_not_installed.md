---
title: "Installation complete, but not installed?"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by theBNich on 2011-05-15
Hello,

I'm having a very weird problem trying to install Ubuntu (11.04 Desktop AMD64).  After running the Ubuntu installer, which seems to complete successfully, the disk appears entirely unmodified after reboot (excluding the MBR).  I've tried installing twice, and this has happened both times.

I have Windows 7 x64 in a ~800GB partition, and I have an unallocated 100GB I'm trying to use to install Ubuntu.  I am using fake RAID 0 with 2x500GB HDDs, which I'm guessing is part of the problem.

I burnt the image to a CD, rebooted, and the installer loads fine.  The first time, I chose the first option to "Install Ubuntu alongside Windows 7".  (BTW, what does this option do?  Is it supposed to install Ubuntu "inside" Windows like Wubi?)

After the installation completed, I got a GRUB Restore error, so I booted into Ubuntu Live.  I looked through my partitions, trying to find the Ubuntu installation, but couldn't.  My 100GB was still unallocated.  I also couldn't find any trace of an Ubuntu installation in the Windows filesystem, in case the installer was supposed to act like Wubi.  Again, I'm not sure what "Install alongside Windows" actually means.  Regardless, my installation seemed to have vanished.  I popped in my Windows DVD, fixed the MBR, and tried again.

This time, I chose the 3rd option to manually set up my installation.  I created a 4GB swap partition, a 20GB root partition, and 76GB /home partition, then clicked continue.  Once it was done, the exact same thing happened: bad MBR, no trace of the installation.  The new partitions that I created didn't even exist: I still had 100GB unallocated.

How is this possible?  I would guess it has something to do with my fake RAID setup, but the installer seemed to detect and read the disks just fine.

---

### Post by theBNich on 2011-05-15
I've maybe made some progress.  Rather than using the Ubuntu installer to create the partitions, I used GParted to create the /, /home, and swap partitions, and it created them.  In the Ubuntu installer, I then selected the corresponding partitions, and it seems to actually be writing the files to the system now.

But now I have a new problem.  Pretty far along into the install, I got a fatal error that GRUB could not be installed to /dev/sda.  I chose to continue the installation without a boot loader, but the next screen said that the installer crashed.

What should I do?  I could probably manually create the GRUB entries, but I doubt that the grub-install was the very last step in the installation, so I probably need a way to do the install without the crash.

---

### Post by Hedgehog1 on 2011-05-15
We need to get a look at your install to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by theBNich on 2011-05-15
Thanks for the response.  Here's the results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/mapper/pdc_bbcjiedcb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_bbcjiedcb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

pdc_bbcjiedcb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

pdc_bbcjiedcb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_bbcjiedcb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

pdc_bbcjiedcb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_bbcjiedcb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,743,407,103 1,743,200,256   7 HPFS/NTFS
/dev/sda3       1,743,409,150 1,953,124,351   209,715,202   5 Extended
Invalid MBR Signature found
/dev/sda5     ? 1,743,409,150 1,743,409,149                   Unknown
/dev/sda6     ? 1,743,409,150 1,743,409,149                   Unknown

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda
the logical partition /dev/sda5 is not contained in the extended partition /dev/sda3
/dev/sda6 ends after the last sector of /dev/sda
the logical partition /dev/sda6 is not contained in the extended partition /dev/sda3

Drive: pdc_bbcjiedcb ___________________ _____________________________________________________

Disk /dev/mapper/pdc_bbcjiedcb: 1000.0 GB, 999999930368 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_bbcjiedcb1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_bbcjiedcb2            206,848 1,743,407,103 1,743,200,256   7 HPFS/NTFS
/dev/mapper/pdc_bbcjiedcb3      1,743,409,150 1,953,124,351   209,715,202   5 Extended
/dev/mapper/pdc_bbcjiedcb5      1,743,409,152 1,785,352,191    41,943,040  83 Linux
/dev/mapper/pdc_bbcjiedcb6      1,944,735,744 1,953,124,351     8,388,608  82 Linux swap / Solaris
/dev/mapper/pdc_bbcjiedcb7      1,785,354,240 1,944,733,695   159,379,456  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_bbcjiedcb1 86B8737BB8736917                       ntfs       System Reserved               
/dev/mapper/pdc_bbcjiedcb2 58467665467643B2                       ntfs                                     
/dev/mapper/pdc_bbcjiedcb5 bc53663d-9a3e-4841-81a1-f6b8f70565fe   ext4                                     
/dev/mapper/pdc_bbcjiedcb6 fb861aa8-9d76-4d35-8669-4cfbd0da6dea   swap                                     
/dev/mapper/pdc_bbcjiedcb7 2ec0dead-5f8e-4763-9cfc-32de6ca23c06   ext4                                     
/dev/mapper/pdc_bbcjiedcb: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_bbcjiedcb3: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sda6: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_bbcjiedcb
pdc_bbcjiedcb1
pdc_bbcjiedcb2
pdc_bbcjiedcb5
pdc_bbcjiedcb6
pdc_bbcjiedcb7

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


========================== pdc_bbcjiedcb5/etc/fstab: ==========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_bbcjiedcb5 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_bbcjiedcb7 /home           ext4    defaults        0       2
/dev/mapper/pdc_bbcjiedcb6 none            swap    sw              0       0

============== pdc_bbcjiedcb5: Location of files loaded by Grub: ==============


 910.7GB: boot/grub/core.img
 893.4GB: boot/initrd.img-2.6.38-8-generic
 910.7GB: boot/vmlinuz-2.6.38-8-generic
 893.4GB: initrd.img
 910.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on pdc_bbcjiedcb3



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/mapper/pdc_bbcjiedcb3: No such file or directory
hexdump: /dev/mapper/pdc_bbcjiedcb3: No such file or directory

```

---

