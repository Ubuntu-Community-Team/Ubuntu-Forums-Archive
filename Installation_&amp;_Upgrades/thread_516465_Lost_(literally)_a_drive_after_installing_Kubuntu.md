---
title: "Lost (literally) a drive after installing Kubuntu"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by saurabh22 on 2007-08-03
Tried installing kubuntu 7.04 on a comp with a single physical drive with three partitions. C:  20gb, D: 30gb and E 30gb 
Installation failed at the point grub was supposed to be installed, saying it couldn't write to hd0. Booted back into windows and E: is now 12.3 Gb, which is what it had been set to automatically partition into but there is no other partition. So somehow e: is now down to 12.3Gb and formatting doesn't help. What happened?

---

### Post by dabl on 2007-08-03
I recommend you download and burn a GParted Live CD from this site: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot the GParted CD to do your partitioning and set the "boot" flag on the partition where you want the Grub bootloader to be installed.  Probably the boot flag is set on a different partition -- you'll need to turn that one off.  Then boot your Kubuntu CD to install again.  Personally I prefer the Alternate Install CD -- gives more visibility and control. :)

---

### Post by zero-9376 on 2007-08-03
I may be reading this wrong but it sounds like you shrank your E drive to install Ubuntu and now in windows you have C-20GB, D-30GB and E-12.3GB. You wont be able to see your new ubuntu partition/partitions from withing Windows, not through explorer at least, you should be able to right click on my computer and go to manage from there find your way to local disk management and you should be able to see your new ubuntu partition. 

Also GParted is on the Ubuntu CD so you can use it from the livecd, from memory its ins sytem-administration.

---

