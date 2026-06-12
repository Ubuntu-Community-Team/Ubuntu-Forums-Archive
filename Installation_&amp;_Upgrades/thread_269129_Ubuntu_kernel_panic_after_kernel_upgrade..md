---
title: "Ubuntu kernel panic after kernel upgrade."
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by deternal on 2006-10-01
[FONT="Arial"]Hi,

After upgrading to the latest kernel (2.6.15.27) I get the following error when booting:[/FONT]

[FONT="Lucida Console"][INDENT]RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) [/INDENT][/FONT]

[FONT="Arial"]I'm running 6.06 (updated from previous release via the alternate install cd).

The system is a Thinkpad T43 and / is on sda4. The system is running dualboot with win xp which boots fine.

The problem started after using the system update util to install the latest kernel + modules etc.

Is there anything I can do besides reinstalling 6.06 and hoping it wont break? :)[/FONT]

---

### Post by pay on 2006-10-01
I'm not on Ubuntu anymore (using gentoo) but wouldn't ```
sudo apt-get install --reinstall linux-kernel-2.6.15.27
```help? That might not be the package's name though..

---

### Post by deternal on 2006-10-02
It might, but since none of the kernels can boot anymore I'm not sure how the exact procedure would be - I'm supposing something like booting from a livecd and chrooting into the on disk environment.

---

