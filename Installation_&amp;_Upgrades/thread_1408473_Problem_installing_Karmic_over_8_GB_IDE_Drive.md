---
title: "Problem installing Karmic over 8 GB IDE Drive"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by jbaserga on 2010-02-16
Hi all,
I am trying to install Ubuntu Karmic in a little workstation with an 8 GB drive. Live CD works fine, gparted can partition the disk, but when it tries to copy the files the installer gives an error (/target is read only).

Disk Utility can see the drive and all test are OK.

The only strange thing I can see is that the disk geometry differs from the one that is declared by the BIOS.

In the console I can see many write errors, but as I said before, disk tests are OK.

Worst part is that Win XP installed flawlessly (so I can discard disk physical problems),

I tried disabling BIOS Autodetection, LBA and putting the geometry by hand with the same results. The disk is Master of the primary IDE controller (I saw a thread that mentioned this as a possible solution for this problem).

Any hints?

Regards

Juan Pablo

---

