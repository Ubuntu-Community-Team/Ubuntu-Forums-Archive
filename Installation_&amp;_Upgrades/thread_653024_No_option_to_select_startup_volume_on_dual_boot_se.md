---
title: "No option to select startup volume on dual boot setup"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by m i k e on 2007-12-29
I just did a fresh install of XP but partitioned my hard drive and installed Ubuntu afterwards.  Everything has gone fine so far except now I don't see any option to boot into Ubuntu when I restart my computer.  When I press the button to get into my boot options (floppy, cd, hd, etc.) it will give me the option of the hard drive but not the specific partition.  What do I need to do to get the boot option to show up?  Thanks.

---

### Post by Pumalite on 2007-12-29
You did not install Grub to the MBR.
You can boot Ubuntu with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or reinstall.

---

### Post by m i k e on 2007-12-29
I guess I'd prefer to just reinstall but how do I install Grub to the MBR?  I thought I did.  What should I do specifically?  Thanks.

---

### Post by Pumalite on 2007-12-29
It installs to MBR by default, so it was probably a bad install. Before proceeding, try to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

