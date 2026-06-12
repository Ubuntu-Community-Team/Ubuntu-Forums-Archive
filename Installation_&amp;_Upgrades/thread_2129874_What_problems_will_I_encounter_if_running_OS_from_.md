---
title: "What problems will I encounter if running OS from USB drive?"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2013-03-27
Hello,

I am currently running Xubuntu 12.04.1 with cgminer (for mining Bitcoin) on a 8GB USB drive on a computer without a HD. The computer is used only for mining. "Universal USB Installer" was used to put Xubuntu on the USB drive.

1. What disadvantages/risks do I face by using a USB drive instead of a HD?

2. Will the Xubuntu system eventually fill up the USB drive with log files, etc.?

3. Does not having a swap partition matter?

Computer info:

    500W Power Supply
    2GB RAM
    Radeon 6750

---

### Post by C.S.Cameron on 2013-03-27
1) If USB2 it will be slower than internal HDD.
    Persistent install not secure. (Full install can be made secure)
    Persistent install not updateable. (Full install is updateable and upgradeable)
    Persistent install will only have max 4GB storage unless persistent partitions are used. (Full install only limited by drive size)
    Drive may wear out after several years if used a lot.

2) Depends on size of drive, Persistent install will quickly fill up if updated, then will not boot.

3) Swap partition mainly used for hibernation. Probably not a good use of space on a small drive.

---

### Post by clay7 on 2013-03-27
Thank you!

---

### Post by TomB19 on 2013-03-27
I've run Ubuntu from a USB flash drive and found it well acceptable.  Long term, however, I understand USB flash can only be written so many times before failing.  USB flash drives don't move the data around, like an SSD.

USB drives are cheap so I recommend you back it up to an identical drive using dd, once in a while and you should be fine.   It's good to have a backup, anyway.

---

### Post by C.S.Cameron on 2013-03-28
When, (if ever), a flash drive fails from too many writes, it becomes read only and no data is lost.
Decent flash drives do have wear leveling.

---

### Post by kyalami321 on 2013-03-28
Several years back, I ran Ubuntu 8 (i think) off an original iPod formatted for disk use for a good month or two while I procrastinated buying a new HDD for my PC since I'd DROPPED mine. My carelessness aside, the system worked pretty well (it was a P4 machine with at least 2GB ram), though I didn't do anything fancy on it. (used Firefox and that's about it). I wouldn't recommend it for long-term use though. It's nice to have as a backup, ready to go when your main system fails. Downtime is minimized to virtual nonexistence if you keep a reliable version of Ubuntu laying around on a flash drive.

---

