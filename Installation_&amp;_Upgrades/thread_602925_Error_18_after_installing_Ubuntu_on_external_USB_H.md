---
title: "Error 18 after installing Ubuntu on external USB HDD"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by German_in_NY on 2007-11-04
What i did was:
Unplug internal HDD (just incase - i do not want this drive touched by linux in any way), plug external 300Gb USB HDD in and start Ubuntu on CD. I then created 2 partitions on the external HDD one for / and one for /swap as required in the installation. (280Gb/20Gb)
I then installed ubuntu to that drive.
After restart and removal of the live CD the screen reads "Starting Grub 1.5" (or something close to that) and "Error 18" in the next line.
This is as far as i get.

How can i solve this problem ?

---

### Post by arkara on 2007-11-04
did you unplug the hdd?
plug the drive back on and then try to reboot.
the thing is that if you unpluged the drive then grub cannot find your partitions and so it gets an error.

---

### Post by German_in_NY on 2007-11-05
Nothing was plugged in or unplugged differently than during the installation process.
Any other ideas ?

---

### Post by bulldog on 2007-11-05
18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

Look for help on this very good site,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

