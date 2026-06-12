---
title: "Upgrade from 12.04 to 14.04, can't choose Windows 7 partition"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by sports fan Matt on 2014-08-22
I upgraded to trusty and all went well but when I restart my computer, I do not see the option to choose Windows 7, which I need for teaching Microsoft and basic computer skills to my clients...How can I fix this so there is an option to select Windows 7 at boot?

---

### Post by kansasnoob on 2014-08-23
What method did you use to upgrade? Hopefully not the Live DVD:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

We'll need more info, please post the boot info from Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sports fan Matt on 2014-08-23
Kansasnoob,
This seems to be a fairly widespread issue.  I upgraded through the update manager.  ============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             64   625,129,340   625,129,277   7 NTFS / exFAT / HPFS
/dev/sda2         625,129,470 1,250,263,039   625,133,570   5 Extended
/dev/sda5         625,129,472 1,242,099,711   616,970,240  83 Linux
/dev/sda6       1,242,101,760 1,250,263,039     8,161,280  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FCE0FAB3E0FA736E                       ntfs       
/dev/sda5        fd61cf15-c6bb-4509-a081-dc96ef731ebf   ext4       
/dev/sda6        0db3bc13-53f3-43ea-80e0-6773a3a6550f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)

---

### Post by kansasnoob on 2014-08-23
Try:

```
sudo update-grub
```

And:

```
sudo apt-get -f install
```

You may have to run update-grub again after apt-get -f install.

---

### Post by sports fan Matt on 2014-08-23
It found it...so it should be okay Monday morning.  What changed with I assume unity to create this whole big issue (I saw a lot of people having similar issues)

---

