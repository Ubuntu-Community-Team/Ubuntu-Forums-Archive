---
title: "Updating Banshee"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by xchecker on 2010-09-30
I am updating Banshee music player from version 1.6.1 to 1.8.  I put the PPA in my Software Sources, used APT-GET to install the updates and confirmed I now have a bunch of 1.8 files and folders on my computer.  Synaptic also shows I have version 1.8 as my current version.  But launching Banshee from my Applications menu, my dock or the Terminal (banshee or banshee-1) still launches version 1.6.

What painfully obvious step am I missing?

---

### Post by Harry33 on 2010-10-01
Xchecker,

You may want to try a clean install:
1. delete (complete removal) all banshee packages (also all the extensions),
2. delete banshee conf folders in the Home Folder:
  - .cache/banshee-1
  - .cache/media-art
  - .config/banshee-1
  - .gconf/apps/banshee-1
3. install the version you want from PPA

---

### Post by xchecker on 2010-10-02
That did it.  Thanks!

---

