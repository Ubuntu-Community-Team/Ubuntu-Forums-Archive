---
title: "Grub won't take over (Vista/XP triple boot)"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by tim75 on 2007-06-21
I have a machine with XP and Vista. XP is on one hard drive and Vista is on another. Each time I attempt to install Ubuntu(7.04), everything goes fine. However when I reboot, it's has if I never installed Ubuntu in the first place. I get the windows boot loader as always. I've done the partitioning part two ways, manual and "guided use contiguous free space". I loaded a ext3 reader for windows and all the files are there in the linux partition but I have no way to boot to them.:confused:

---

### Post by louieb on 2007-06-21
Kinda weird that the MBR did not get changed to point to the GRUB program /boot/grub/stage2.  Look at the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/"). And check out the   [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/")
It may be that the installer got confused and changed the MBR of the 2nd hard drive.  


---

### Post by ckempo on 2007-06-21
louieb seems right, but see if there's anything in here that helps you too: [http://ubuntuforums.org/showthread.php?t=476855]("http://ubuntuforums.org/showthread.php?t=476855")

---

