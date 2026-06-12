---
title: "Can't mount second HD after 8.04 Hardy upgrade."
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Darthnix on 2008-05-20
After upgrading to hardy, I cant seem to mount my second hard drive. I can see the drive when I use gparted but it has a warning saying "Couldn't find a valid file system superblock." Also if I boot up using my old 7.04 live disk, I can mount the drive with no problem. Any Ideas?

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91449144

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4660 37431418+ 83 Linux
/dev/sda2 4661 4865 1646662+ 5 Extended
/dev/sda5 4661 4865 1646631 82 Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000006b6

Device Boot Start End Blocks Id System
/dev/sdb1 1 19317 155163771 83 Linux
/dev/sdb2 19318 19457 1124550 5 Extended
/dev/sdb5 19318 19457 1124518+ 82 Linux swap / Solaris

Disk /dev/sdb is the drive in question.

If I pull up gparted, I can see the drive but it has a warning flag on it that says the following:

e2label: No such file or directory while trying to open /dev/sdb1
Coundn't find valid filesystem superblock.

dumpe2fs 1.40.8(13-Mar200
dumpe2fs: No such file or
directory while trying to open /dev/sdb1

Unable to read the contents or this filesystem!
Because of this some operations may be unavailable.

---

### Post by logos34 on 2008-05-20
usually it recommends you run

**sudo e2fsck -b 8193 /dev/sdb1**

---

### Post by Darthnix on 2008-05-20
Results from that.

********************:~$ sudo e2fsck -b 8193 /dev/sdb1
e2fsck 1.40.8 (13-Mar-2008)
e2fsck: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by Darthnix on 2008-05-21
Well I think im going to load Gutsy Gibbon back on to my machine. Ill try Hardy Heron again after it matures a bit more. I am also having issue with my server not booting up half the time. Never had this issue before.

---

### Post by lauchazombie on 2008-05-21
i had this problem when i tried a fresh install like a mont ago, now i tried to upgrade from 7.10 and the same happened...someone knows how to fix it?

---

### Post by Tyler H on 2008-05-22
This seems to be a real issue. I can manually mound it the CLI with quite a bit of work, but it will not mount automatically even after modding the fstab files. (in reference to my second hdd)

---

### Post by Darthnix on 2008-05-22
Well I went back to 7.10 and now all is well. I'm wondering since all of my drives are IDE if that has something to do with this issue.

---

### Post by lauchazombie on 2008-05-22
well las time it happened to me i had to downgrade to 7.10, but now i think this bug must be fixed so please if some coder reade us :P

---

### Post by Rog on 2008-06-01
I had a similar problem when I upgraded yesterday.  I suspect that the new kernel might be assigning different /dev/sdxy values to different disks and partitions than previous.

Has anyone raised a bug for this?

- Rog

---

### Post by lauchazombie on 2008-06-05
> **Rog said:**
> I had a similar problem when I upgraded yesterday.  I suspect that the new kernel might be assigning different /dev/sdxy values to different disks and partitions than previous.

Has anyone raised a bug for this?

- Rog
 i dont think thats the problem couse i still have sdb, i dont have sdb1 so its a problema about recognizing partitions

---

