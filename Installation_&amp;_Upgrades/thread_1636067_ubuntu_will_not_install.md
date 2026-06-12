---
title: "ubuntu will not install"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by kitoisara on 2010-12-02
Well i tryed to ubuntu wubi install and ubuntu has a messed up screen and i tryed the alternate install but when i set up my partition it always says partition failed and it aborts the partition resizing so i havent been able to get it to install i have an older laptop its about 3 year old hp pavilion with amd turion64x2 processor windows vista home premium is there anything else i can try to get ubuntu to install

---

### Post by bcbc on 2010-12-02
> **kitoisara said:**
> Well i tryed to ubuntu wubi install and ubuntu has a messed up screen and i tryed the alternate install but when i set up my partition it always says partition failed and it aborts the partition resizing so i havent been able to get it to install i have an older laptop its about 3 year old hp pavilion with amd turion64x2 processor windows vista home premium is there anything else i can try to get ubuntu to install

Try this [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If you have a specific graphics card e.g. nvidia, then using nomodeset helps. You may have another issue - post back more hardware details or describe your errors in more detail if the graphics thing or boot option workarounds don't work

---

### Post by kitoisara on 2010-12-02
i have a nvidia card but its my partition when i get to the screen that tells me to set it up i do and when its setting up it says partition failed and i dont know why its doing that

---

### Post by bcbc on 2010-12-02
Vista should be able to partition for you - disk utility. Make sure you don't already have 4 primary partitions (max). If you have 3, create space using the disk utility and then create an extended partition in the space, and 2 logicals within that for Ubuntu root and swap.

You can boot a live CD and use Gparted to create the extended and logicals etc. once Vista has made the space.

---

