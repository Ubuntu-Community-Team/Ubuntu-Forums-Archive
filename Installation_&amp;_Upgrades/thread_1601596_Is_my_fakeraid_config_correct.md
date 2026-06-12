---
title: "Is my fakeraid config correct?"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by cybershark5886 on 2010-10-20
Hello all,
 
I recently have set up a hardware/fake raid 1 array with two 2TB disks in a HP Compaq dc5750 Microtower, and I originally was concerned that Ubuntu (or any Linux distro) would not run on the hardware when RAIDed since its install guide says it only supports Windows XP SP2 and accompanying RAID drivers, etc. Anyway, for the heck of it after reading the Ubuntu fakeraid setup page I decided to try it anyway with Ubuntu 10.10 and rather than the nightmare I was expecting with installing dmraid and all the other manual configuration steps it did an auto install that seemed to work magically, and installed dmraid for me. So everything seems peachy, but I'm not experienced enough with RAID in linux to tell if my RAID 1 array is indeed working correctly and is replicating.
 
Here are a few of the results I am seeing with various commands on discovering disks & mounts.
 
*cat /etc/fstab* shows this for the mounted partitions:
 
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_jegeah2 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_jegeah5 none            swap    sw              0       0
 
```*ls -l /dev/mapper* shows:
```
 total 0
crw------- 1 root root 10, 59 2010-10-19 15:55 control
lrwxrwxrwx 1 root root      7 2010-10-19 15:55 pdc_jegeah -> ../dm-0
lrwxrwxrwx 1 root root      7 2010-10-19 15:55 pdc_jegeah2 -> ../dm-2
lrwxrwxrwx 1 root root      7 2010-10-19 15:55 pdc_jegeah5 -> ../dm-3

```*sudo blkid* shows:
 
```

/dev/sda: TYPE="promise_fasttrack_raid_member" 
/dev/sdb: TYPE="promise_fasttrack_raid_member" 
/dev/mapper/pdc_jegeah2: UUID="0853d7e3-fb0a-4a5c-8398-dd6cd93702ee" TYPE="ext4" 
/dev/mapper/pdc_jegeah5: UUID="9fcb53d5-e5ca-452e-a273-29fe03d9a7f9" TYPE="swap"

```*sudo blkid -p /dev/* on sd* and dm* show:
 
```

/dev/sda: PTTYPE="dos" TYPE="promise_fasttrack_raid_member" USAGE="raid" 
/dev/sdb: PTTYPE="dos" TYPE="promise_fasttrack_raid_member" USAGE="raid" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
 
/dev/dm-0: PTTYPE="dos" 
/dev/dm-2: UUID="0853d7e3-fb0a-4a5c-8398-dd6cd93702ee" VERSION="1.0" TYPE="ext4" USAGE="filesystem" 
/dev/dm-3: UUID="9fcb53d5-e5ca-452e-a273-29fe03d9a7f9" VERSION="2" TYPE="swap" USAGE="other" 

```And *df* shows my primary partition as pdc_jegeah2:
 
```

/dev/mapper/pdc_jegeah2
                     1919593472  68855972 1753227820   4% /
none                   1987792       264   1987528   1% /dev
none                   1993508       312   1993196   1% /dev/shm
none                   1993508        88   1993420   1% /var/run
none                   1993508         0   1993508   0% /var/lock
none                 1919593472  68855972 1753227820   4% /var/lib/ureadahead/debugfs

```Lastly, *sudo fdisk -l* shows:
 
```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c17ef
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          242789      243153     2928641    5  Extended
/dev/sda2               1      242789  1950193664   83  Linux
/dev/sda5          242789      243153     2928640   82  Linux swap / Solaris
 
Partition table entries are not in disk order
 
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c17ef
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          242789      243153     2928641    5  Extended
/dev/sdb2               1      242789  1950193664   83  Linux
/dev/sdb5          242789      243153     2928640   82  Linux swap / Solaris
 
Partition table entries are not in disk order
 
Disk /dev/dm-0: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c17ef

```So, with all that information, from what I can tell it looks to be set up correctly. But I do have a few questions about some things I don't understand. The /dev directory shows my sda and sdb physical drives, but Ubuntu is mounting /dev/mapper/pdc_jegeah2. So are block devices shown in /dev/mapper a "virtual" representation of the two logically RAIDed drives together? If you'll notice on the fdisk -l output sda and sdb have the **same** disk identifier "0x000c17ef". Is that supposed to happen? Is that related to the hardware/"fake" RAID config?
 
Also, how can I confirm that my data is being replicated between both disks? Should I mount sda and sdb and look at both of them, or will that cause a problem with pdc_jegeah2 already mounted?
 
My last question has to do with what gparted is showing me for both 2TB disks. Below are two screen shots of a reported error, and I'm not sure what it is indicating:
 
[ATTACH]172929[/ATTACH]
 
[ATTACH]172930[/ATTACH]
 
It shows the exact same thing for sdb. Is it saying that sda and sbd's primary partitions are not mounted because the "virtual" RAID disk parition /dev/mapper/pdc_jegeah2 is mounted instead?
 
Sorry for the newbie questions, I hope I have given sufficient data to help you address this question.
 
Thank you,
 
Josh

---

### Post by ronparent on 2010-10-20
Josh - Try writing to terminal 'blkid'. This  should show the recognized raid partitions. Also in terminal write 'sudo dmraid -ay'. If everything is normal it should show your raid as already activated. 

10.10 is the easiest install to date to a raid drive. Normally dmraid will be installed with the install and your raids will be automatically recognized. If that is not the case it should be easily fixable. Of concern is that sdb doesn't seem to mirror sda in gparted but it does with fdisk. Gparted should have been updated with the release of 10.10, but, if it wasn't, installing kpartx should allow gparted to see the raid as a raid.

---

### Post by cybershark5886 on 2010-10-20
> **ronparent said:**
> Josh - Try writing to terminal 'blkid'. This  should show the recognized raid partitions. Also in terminal write 'sudo dmraid -ay'. If everything is normal it should show your raid as already activated. 

10.10 is the easiest install to date to a raid drive. Normally dmraid will be installed with the install and your raids will be automatically recognized. If that is not the case it should be easily fixable. Of concern is that sdb doesn't seem to mirror sda in gparted but it does with fdisk. Gparted should have been updated with the release of 10.10, but, if it wasn't, installing kpartx should allow gparted to see the raid as a raid.

Okay, my output for 'blkid' is:

```
/dev/sda: TYPE="promise_fasttrack_raid_member" 
/dev/sdb: TYPE="promise_fasttrack_raid_member" 
/dev/mapper/pdc_jegeah2: UUID="0853d7e3-fb0a-4a5c-8398-dd6cd93702ee" TYPE="ext4" 
/dev/mapper/pdc_jegeah5: UUID="9fcb53d5-e5ca-452e-a273-29fe03d9a7f9" TYPE="swap"
```And when I did 'sudo dmraid -ay' I got:

```
RAID set "pdc_jegeah" already active
RAID set "pdc_jegeah2" already active
RAID set "pdc_jegeah5" already active

```Also, yes, installing kpartx did show me the pdc_jegeah raid disk in gparted after I installed it. That's good. Can I still mount sda and sdb though to manually check that some files I downloaded were replicated, or will that cause a problem with the pdc_jegeah2 partition being mounted?

Thanks so much for your help!

~Josh

P.S. I'm glad 10.10 made this easy for me so far.

---

### Post by ronparent on 2010-10-20
As long as the raid isn't broken, don't try to hard to break it! You will get the message if the drive stops mirroring correctly. Handle that problem if you get to it. Best of luck to you. 

Ron

Edit: Besides, you can always boot to a live cd, deactivate the raid (sudo dmraid -ny), and use nautilus to examine your disk side by side.

---

### Post by cybershark5886 on 2010-10-21
Excellent. Thank you. I'm all set up now.

Regards,
 
Josh

---

