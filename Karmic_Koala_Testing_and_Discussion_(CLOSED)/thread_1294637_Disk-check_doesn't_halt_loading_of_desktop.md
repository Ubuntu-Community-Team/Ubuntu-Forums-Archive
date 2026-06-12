---
title: "Disk-check doesn't halt loading of desktop"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ShadowTek on 2009-10-18
I just had one of my hard drives fail to mount upon rebooting my computer. I didn't realize this until I tried to run a program that depended on files in that disk, at which point I received an error. I then tried to e2fsck the disk, but it said that the disk was busy. I then rebooted my computer into recovery mode and, for a brief flash of an instant, saw that one of my disks had reached the number of boots that it was scheduled to do a disk-check after.

Apparently, the scheduled disk-checks do not halt the loading of the desktop in Karmic, whereas it did in previous versions. Is this intended, or is this a bug?

I think there should at least be some kind of declared warning to the user of what is going on, and I prefer the old method of preventing the loading of the desktop until all disk-checks are complete.

Here is the fstab entry that I'm using with this disk:
```
UUID=(snip)    /media/DL  ext3  relatime,errors=remount-ro  0  2
```

---

### Post by isaiasmy on 2009-10-29
I'm having exactly the same problem and it is quite annoying. Some solution would be really desirable.

---

