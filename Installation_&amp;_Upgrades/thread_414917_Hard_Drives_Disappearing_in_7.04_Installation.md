---
title: "Hard Drives Disappearing in 7.04 Installation"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ignignokt00 on 2007-04-20
Howdy.  I installed Feisty Fawn anew by wiping my main NTFS drive (formerly of Windows occupation) and formatting it all as ext3, with 2gb of swap.  
When I boot from the Live CD, all of my disks are visible, including the NTFS partition on my secondary drive as well as the old Ubuntu Edgy ext3 partition on that same second disk.  I can browse them, see everything, whatever.

During install, I tell it to mount /dev/sda1 at /, and /dev/sdb5 at /media/whatever.  However, when I boot, I get:
> /bin/sh: can't access tty; job control turned off
and 
> fsck died with exit status 8
I've searched these messages and nothing helped.
I can hit control+D to leave the maintenance CLI, and boot into Ubuntu.  The primary partition shows up just fine, but no other partitions show up, not even the other ext3 one.
If I open a terminal and type "sudo mount /dev/sdb5 /media/ntfspart", it says that special device /dev/sdb5 doesn't exist.  Same with /dev/sdb1, the old ext3 partition.
And when I plug in a third drive, IDE, it doesn't appear either.
Help, please?

Both HDD's are SATA.

---

### Post by ignignokt00 on 2007-04-20
bump :\

---

