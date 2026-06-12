---
title: "Changing Size Of A Partition Made With &quot;dd&quot;"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by charlesviper on 2009-12-03
Hello all,

I cloned a 160GB SATA HDD to a 250GB SATA HDD. Both boot up fine; all settings are intact. The two devices are /dev/sda (on SATA port '0' on my motherboard, this is the 160GB HDD) and /dev/sdb (on SATA port '1'). If I go to System -> Administration -> GParted, this is what I see:

```
/dev/sda1
file system: ext3
mount point: /
size: 143.32 GiB
flags: boot

/dev/sda2
file system: extended
size: 5.73 GiB

/dev/sda5
file system: linux-swap
size: 5.73 GiB
``````
/dev/sdb1
file system: ext3
mount point: /
size: 143.32 GiB
flags: boot

/dev/sdb2
file system: extended
size: 5.73 GiB

/dev/sdb5
file system: linux-swap
size: 5.73 GiB

unallocated
size: 84.83 GiB
```I'd like to extend the ext3 file system on /dev/sdb1 to include the 84.83 GiB of unallocated space. On the "sdb" drives, the 'used space' and 'free space' data isn't shown, and Ubuntu says that because there is no mount point the filesystem cannot be read. I am attempting this by booting off the 160GB drive, opening GParted, and performing the changes on the 250GB drive. If I select "unmount", nothing happens -- I'm guessing the drive thinks it is already unmounted.

Any ideas?

EDIT: when I used "dd", I put the 250GB HDD on SATA port 1 (with the 160GB on SATA port 0) and ran the command:

```
sudo dd if=/dev/sda of=/dev/sdb bs=1024M
```

This isn't a copy made within a drive, it was a bit for bit backup between two drives of different sizes. I'd like to resize the ext3 partition on the drive I copied the data onto, /dev/sdb.

Any help would be really appreciated.

---

### Post by charlesviper on 2009-12-03
Here's a copy of the "fdisk -l"

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001442f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18709   150280011   83  Linux
/dev/sda2           18710       19457     6008310    5  Extended
/dev/sda5           18710       19457     6008278+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001442f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18709   150280011   83  Linux
/dev/sdb2           18710       19457     6008310    5  Extended
/dev/sdb5           18710       19457     6008278+  82  Linux swap / Solaris
```

---

### Post by oldfred on 2009-12-03
IF anything it seems that dd does too good of a job copying. It is meant to copy from same size to same size and resets you larger hard drive to the same size as your smaller.

I saw this several months ago. One poster solved it with a tool downloaded from the hard drive manufacturer. 

I also copied this and saved it but I am not sure if it was for this type of problem nor do I know if it works or has a newer version. Or more of a place to start looking rather than a simple solution.

P.S. Some time ago, i bought the 1000Gb HDD (the sdc). Only kubuntu 9.04 was able to see and use it correctly (as a 1000Gb HDD). XP and the BIOS were able to see a only 32Mb HDD (maybe the cache?).
After many unsuccesful adventures, i wrote an email to the motherboard vendor (Gigabyte) and they answered me this:
Quote:
...Thank you for your kind mail and inquiry. About the issue you
mentioned, please try to made a DOS bootable USB stick.

2. Put this application on it:
[http://hddguru.com/content/en/software/2005.10.02-MHDD/](http://hddguru.com/content/en/software/2005.10.02-MHDD/)
[http://hddguru.com/content/en/software/2007.07.20-HDD-Capacity-Restore-Tool/](http://hddguru.com/content/en/software/2007.07.20-HDD-Capacity-Restore-Tool/)

3. Boot to DOS.

4. Run MHDD

5.Selecte the drive.

6. Typed HPA into the prompt

7.Selected permanent HPA

8. Entered the value for the LBA number.(Please contact harddisk manufacturer)

9.It should back full size.

---

### Post by charlesviper on 2009-12-03
Thanks Fred. One thing, the operating system (and GParted) show 90GB of unallocated space, and I can successfully make a new partition. The OS is seeing all 250GB, I just need a way to format that.

I'm downloading GParted's live USB stick. I'll see if that works.

---

### Post by oldfred on 2009-12-03
I hope gparted will see it and possibly correct it but your fdisk has the same for both drives:

Units = cylinders of 16065 * 512 = 8225280 bytes

---

### Post by charlesviper on 2009-12-04
oldfred, thanks for trying to help me out with this. If I load up GParted, I can make a new partition and everything -- but the swap file is in the middle of the drive. If I delete the swap file, I can extend the ext3 partition to fill the drive (leaving a little space at the end for a new Extended + Linux-Swap partition). However, if I do this, GRUB has an error when booting: it says error #15. Any suggestions?

---

### Post by oldfred on 2009-12-04
Withour seeing your fstab it is probably wrong. It has an entry for your swap and the UUID must be the swap partition's UUID. If you delete that partition and then create another new swap it does not automatically update the UUID.

use blkid to see UUID and edit fstab to have the correct UUID for the new swap.

If that is not the issue post back and we will have  to look at all the details of your boot process.

---

