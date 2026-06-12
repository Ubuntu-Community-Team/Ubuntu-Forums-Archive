---
title: "Can't get gparted to work"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by glendavee on 2007-07-07
I'm trying to make a new partition on my hard drive. Booting from the installation CD, and using gparted, job fails when I try to implement the change. Error message is "check filesystem for errors and fix them"
I've also tried by installing gparted using synaptic on my live system, but in this case all the menu options on gparted are greyed out. I've tried to unmount the drive, but umount won't let me.
Where am I going wrong???

---

### Post by diatribe on 2007-07-07
try running fsck on the (unmounted) drive first

---

### Post by glendavee on 2007-07-07
I've booted from installation CD, and unmounted the drive. fsck returns
"e2fsck: need terminal for interactive repairs"

---

