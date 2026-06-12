---
title: "Copy/Clone Partial Hard Drive"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by theone964 on 2011-09-07
Hi, Im trying to backup a windows hard drive, it's 150GB but only 15GB are used. I've cloned hard drives using dd before but that cloned the whole hard drive and whenever i reinstalled the image i installed it to a hard drive that was exactly the same size or bigger.

I was wondering if 1) I could copy/clone only the used portion (15GB,personal files and windows installation) of the hard drive and 2) if when i put an image back on a hard drive can i put it on a smaller drive ( I don't see how if the source is bigger than the target, but maybe you could safely shrink the source?)

I dont know if this makes a difference or not but its a Windows XP installation and a Ubuntu 10.04 desktop i'm using.
I'm doing this because i lost my windows CD and my POS software CD

---

### Post by haqking on 2011-09-07
> **theone964 said:**
> Hi, Im trying to backup a windows hard drive, it's 150GB but only 15GB are used. I've cloned hard drives using dd before but that cloned the whole hard drive and whenever i reinstalled the image i installed it to a hard drive that was exactly the same size or bigger.

I was wondering if 1) I could copy/clone only the used portion (15GB,personal files and windows installation) of the hard drive and 2) if when i put an image back on a hard drive can i put it on a smaller drive ( I don't see how if the source is bigger than the target, but maybe you could safely shrink the source?)

I dont know if this makes a difference or not but its a Windows XP installation and a Ubuntu 10.04 desktop i'm using.
I'm doing this because i lost my windows CD and my POS software CD

is it a partition of 15gb or one big partition of 150Gb with only 15 used ?

i was gonna say [clonezilla]("http://www.clonezilla.org")

---

### Post by theone964 on 2011-09-07
Unfortunately this PC was created before i understood what partitions were :( one big 150GB partition

---

### Post by theone964 on 2011-09-07
just had a thought LOL....Could i SAFELY resize a windows partition? what software would i use....it can be windows or linux it doesn't bother me just yet to resize

---

### Post by haqking on 2011-09-07
> **theone964 said:**
> just had a thought LOL....Could i SAFELY resize a windows partition? what software would i use....it can be windows or linux it doesn't bother me just yet to resize


yes you can resize it, lots of tools out there to do it.

try [gparted]("http://gparted.sourceforge.net/index.php") it is a live cd so OS agnostic.

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

then boot to it change things around to suit.

then use [clonezilla]("http://www.clonezilla.org") to clone the new partition ;-)

---

### Post by Hakunka-Matata on 2011-09-07
Although gparted will resize your windows partition, many people recommend against resizing windows partitions with gparted.  GParted is known to have caused problems in some instances.  There are a lot of opinions on this topic, so expect some FMs to reply and contend it's fine to use gparted.

I suggest rather to resize your windows partition using windows tools.  The choice (and repair) are owned by you, your decision.

Boot into your windows OS and use Disk Management tool to first Defragement the drive, twice at least.  Then use Disk Manager to resize your windows partition, it's safer that way.

Do I have to mention backups, windows repair discs, important data on windows partition???

good luck

---

### Post by Mark Phelps on 2011-09-08
If you want to SAFELY resize your Windows partition, then Google for EASEUS Partition Master or for Partition Wizard.  Both are free downloads, and both can handle NTFS partitions without problems.

---

### Post by YesWeCan on 2011-09-09
I like to keep things really simple. I'd just copy the start of the disk. Then I would be able to copy it back to another disk and it would boot and look identical.

I'd run sudo sfdisk -luS to determine the last sector address of the last partition I want to copy.

_Example_: I want to make a restorable copy of my XP system. It is in sda1.
```
ubuntu@ubuntu:~# sudo sfdisk -luS /dev/sda

Disk /dev/sda: 24321 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 [COLOR="Red"]226326910[/COLOR]  226326848   7  HPFS/NTFS

```
The last sector of my Windows is 226326910. Sector addresses start at 0 so the minimum no. of sectors to copy is 226326910+1=226326911.
But no need to be exact, just use a conveniently larger number like 230000000.

```
sudo dd if=/dev/sda bs=512 count=230000000 > windows.img
```

Simple as that.

To restore to a new disk, sdx (this will erase any existing data on it):

```
sudo dd if=windows.img of=/dev/sdx conv=notrunc
```

---

