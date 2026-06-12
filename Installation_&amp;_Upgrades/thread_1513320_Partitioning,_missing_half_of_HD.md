---
title: "Partitioning, missing half of HD"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by ndyguy on 2010-06-19
I recently upgraded from XP to Kubuntu, and I noticed that during partitioning (during installation) I could only partition 80GB out of the 160GB I should have.  I don't know if this will help but:
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  2.8G   64G   5% /
none                  719M  296K  718M   1% /dev
none                  723M     0  723M   0% /dev/shm
none                  723M   92K  723M   1% /var/run
none                  723M     0  723M   0% /var/lock
none                  723M     0  723M   0% /lib/init/rw
none                   71G  2.8G   64G   5% /var/lib/ureadahead/debugfs
/dev/sdb1             7.1G  5.8G  964M  86% /media/disk

```

```
sudo fdisk -l | grep Disk
Disk /dev/sda: 80.0 GB, 80026361856 bytes
Disk identifier: 0x000ed7ef
Disk /dev/sdb: 8004 MB, 8004132864 bytes
Disk identifier: 0x000a154d
```

Also, at Grub there are several old Ubuntu selections from a previous install I did a long time ago; not the next oldest 1 or 2 Kubuntu versions, older Ubuntu versions.

Any ideas?

---

### Post by darkod on 2010-06-19
The older installs would be there if you never deleted them (the partitions). XP wouldn't be able to see them so they can sit there a while. Now Kubuntu detected them and added them to the boot menu.

If you open Gparted what does it say for the hdd and the partitions?

---

### Post by Chame_Wizard on 2010-06-19
How the heck can you missing half of the HD space?
You can indeed check with Gparted why 80 GiB is missing.

---

### Post by oldfred on 2010-06-19
Fdisk says it is 80GB, what does BIOS see the drive as?

---

### Post by ndyguy on 2010-06-19
> **oldfred said:**
> Fdisk says it is 80GB, what does BIOS see the drive as?

That was a good idea.  I checked the BIOS and it says I have a WDC WD800BB-22JHC (80GB, sda) and a WDC WD0EB-28CGH2 (8GB, sdb).  The first one is probably correct, but the second one shouldn't be 8GB.  Is the BIOS misidentifying it?  I never thought about it til now, but upon opening the case I do have two hard drives.

I know it's supposed to be 160GB total (the sticker on the case told me so ;) ) as I bought it new about 5 years ago and haven't modified the hardware.  Maybe something happened to one of the drives?

---

### Post by darkod on 2010-06-19
I thought the 8GB is a SSD or memory card.

Do you have a desktop? It's highly unlikely you would have 8GB disk in a desktop.

Lets search for that model number the BIOS gave you.

Meanwhile open the case and check the sticker on both disks, and try to find out the model number and the size should also be on the sticker. If not google with that model number.

---

### Post by darkod on 2010-06-19
PS. On the WDC website there is no WD0EB model, but there is WD100EB model which it says is 10GB IDE disk (PATA).

Double check model and size on the sticker on it.

---

### Post by ndyguy on 2010-06-19
> **darkod said:**
> PS. On the WDC website there is no WD0EB model, but there is WD100EB model which it says is 10GB IDE disk (PATA).

Double check model and size on the sticker on it.

Thanks, I'll check the stickers tomorrow.  P.S. You were correct, I had a typo.  It should have been WDC WD80EB-28CGH2.

---

### Post by ronparent on 2010-06-19
I have seen this before. The client insist he bought a single ie 160 Gb hard drive with XP installed. He installed Ubuntu and ended up with only 80 Gb. Once prompted to open the case he discovers two drives of 80 Gb each. The upshot is that the seller sold him a system with raid0. Once Ubuntu is installed to the "full" drive he now has one 80 Gb drive with the system and a second drive essentially unformatted. The only complication is that there is probably raid meta data on both disks. The raid possibility should probably be checked out before the situation gets too confused.

---

### Post by darkod on 2010-06-20
It would be good if it was that. The stickers on the disks say WD800BB (a 80GB disk) and WD80EB, one zero less, would translate to 8GB disk, but the WD website doesn't have that model number at all. Smallest size is WB100EB, a 10GB disk.

Look at the first post, sda1 says 71GB (usable), sdb1 says 7.1GB.

It all points that the second disk is 8GB.

In 5 years you never noticed you don't have a total of 160GB space???

---

### Post by ndyguy on 2010-06-20
> **darkod said:**
> It would be good if it was that. The stickers on the disks say WD800BB (a 80GB disk) and WD80EB, one zero less, would translate to 8GB disk, but the WD website doesn't have that model number at all. Smallest size is WB100EB, a 10GB disk.

Look at the first post, sda1 says 71GB (usable), sdb1 says 7.1GB.

It all points that the second disk is 8GB.

In 5 years you never noticed you don't have a total of 160GB space???

darkod is correct (mostly).  The BIOS gave me those part numbers; I didn't check the stickers until today.  But yes, I'm not sure when it happened, but at some point one of the 80GB hard drives got replaced by either me or someone else.  I suppose if you don't use 160GB you don't notice it missing.

In short, sorry for wasting everyone's time.  I had an 80GB and an 8GB hard drive installed.  And despite what the WDC website says (I checked too), the 8GB HD is a WD80EB-28CGH2.

Thanks for the help everyone.

---

