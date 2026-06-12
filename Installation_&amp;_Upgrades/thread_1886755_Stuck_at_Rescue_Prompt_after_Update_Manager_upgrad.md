---
title: "Stuck at Rescue Prompt after Update Manager upgrade from 9.10-&gt;10.04"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by ChaozUT on 2011-11-25
Hi, I created an account because I've been trying to solve this issue and none of the previous posts I found seem to be exactly the issue I am having. Any help would be appreciated.

Background:
- Yesterday I decided to upgrade Ubuntu from 9.10->10.04 because the update manager had been bugging me for weeks.
- I did not configure this system myself and the person who did no longer works here.

Problem:
- During upgrading there was an option to select the location of GRUB. I picked the drive I saw on the list that had /boot somewhere in the description. The other 6-7 drives were almost identical (I don't remember the details but apparently they are 6-7 1.5TB drives in a raid setup).
- After rebooting (last step in the updater install), OS was stuck at the loading screen (4 dots moving on screen for 2+ hours.
- I hard reset the system and now shows an error saying "grub_puts_" was not found and then shows the grub rescue prompt.

Things I have tried and learned:
- "ls" at the rescue prompt shows a list of devices. Trying to "ls" into (hd5,1) and (hd5,2) gives a "bad filename" error. Trying to "ls" into anything else gives "unknown filesystem" error.
- "set" shows that prefix=(UUID=b081....3b)/grub and root=(UUID...) <-- later it seems that this is the UUID of hd5,1 (sdf1).
- I can't set prefix/root to another location since everything else is "unknown filesystem"
- I later booted into the 10.04 liveCD and tried recovering grub using the guide [HERE]("http://ubuntuforums.org/showthread.php?t=1195275"). The grub-install on sdf completed without errors but I still have the same issue when I tried to reboot.
- Lastly I downloaded a boot info script and ran it. It is a bit confusing because the "Boot Info Summary" says Grub2 is installed in MBR of sda and that no boot loader is installed in the MBR of /dev/sdf. But later it shows sdf1 as ext4 filesystem with Grub2 boot sector type. Here is the output:

> Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (UUID=b081ffab-a0db-4d17-969b-a8ac4899ec3b)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => No boot loader is installed in the MBR of /dev/sde.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdd2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdf1 and looks at sector 392063 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 1 for /grub.
    Operating System:  
    Boot files:        

sdf2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sda2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdb2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdc2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sdd2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sde _____________________________________________________________________

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1                  63     1,959,929     1,959,867  fd Linux raid autodetect
/dev/sde2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *             63     1,959,929     1,959,867  83 Linux
/dev/sdf2           1,959,930 2,930,272,064 2,928,312,135  fd Linux raid autodetect


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sda2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdb1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sdb2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdc1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sdc2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdd1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sdd2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sde1        3444b803-6d39-fac1-486d-98e3a3ed0bff   linux_raid_member 
/dev/sde2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 
/dev/sdf1        b081ffab-a0db-4d17-969b-a8ac4899ec3b   ext4       
/dev/sdf2        15135403-8c15-00bd-4955-6804d345d67a   linux_raid_member 

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/b081ffab-a0db-4d17-969b-a8ac4899ec3b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdf1        /mnt                     ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

Our SVN and Bugzilla is hosted on this system so it is very important that I fix this asap and don't F up the data on any of the drives :( I feel like I have tried everything. Any help would be appreciated. Alternatively, is there some way to connect another drive to boot to and somehow view all this data on the other drives?

Thanks in advance.

---

### Post by BC59 on 2011-11-25
Because as I see you have problems with Grub, there is an app called Boot-Repair.

You can download the bootable .iso file and install it in a USB through StartUp Disk Creator.

Then boot with the USB and follow the instructions:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ChaozUT on 2011-11-25
> **BC59 said:**
> Because as I see you have problems with Grub, there is an app called Boot-Repair.

You can download the bootable .iso file and install it in a USB through StartUp Disk Creator.

Then boot with the USB and follow the instructions:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks I shall try that.

---

### Post by ChaozUT on 2011-11-25
Update:

I have tried booting the boot-repair disk. The first time I just clicked the recommended repair and it looked like it installed GRUB on every single drive. After that, before rebooting I was actually able to see the raid drive and all it's content through the GUI. However, upon rebooting it was still stuck at grub rescue.

Here is the paste info linked after the first repair: [http://paste.ubuntu.com/749509/](http://paste.ubuntu.com/749509/)

It didn't work the first time so I tried again, but now after rebooting the pc shows "no operating system detected"... :(

Here is the paste info linked after the second attempt:
[http://paste.ubuntu.com/749528/](http://paste.ubuntu.com/749528/)


The main thing is, on the second paste info it doesn't list the dev/md drives anymore...

---

