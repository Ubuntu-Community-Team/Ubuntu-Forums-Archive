---
title: "Dual installation"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by Howardvan on 2005-09-22
I have a computer with 2 hard drives.  XP is installed on the master.  A Fedora core is installed on the second drive.  I have a ubuntu CD for installation.  I want to replace the Fedora core completely.  How do I do that [without disturbing the XP system]?  I'm probably in way over my head in attempting this.

Thanks,   Howardvan

---

### Post by aysiu on 2005-09-22
It's a lot easier than you think.
Just install Ubuntu.
When you're asked whether you want to wipe the whole hard drive clean or manually edit the partition table, pick the latter.
Select the currently Fedora Core partition to be formatted as ext3 and mounted as /
Then, install Grub to the MBR.
That's it.

---

