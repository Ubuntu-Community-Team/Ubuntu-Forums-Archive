---
title: "Problem with &quot;Installation/FromHardDriveWithFloppies&quot;"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by k3vin187 on 2007-02-10
I'm currently installing Ubuntu on an older laptop and I can't figure out 1 step in the installation.  In pt 3 of setting up the destination drive it says "Load the usb modules from the secondary floppy, usbcore first, using the command 'insmod'".  I know this is a newb question but i can't figure out how to do this (probably because this is my first ubuntu install).  I can get tomsrtbt to run fine but I don't know how to load the modules from the floppy and I can't find any documentation anywhere, on any site.  Hope someone can help.

---

### Post by amp_man on 2007-02-10
Okay, I love Ubuntu, but if you need to use a floppy install, you're probably running older hardware, right? In that case, I'd definately go with Debian (which has a 3-floppy based net-installer). Either that or else download the Knoppix ISOs and create a pair of floppys with the knoppix initrd, and use the Bootfrom= option to boot from an iso on the hard drive. BTW, the install from floppys page doesn't work with any ubuntu version past 5.04, afaik

---

### Post by k3vin187 on 2007-02-11
hey thanks I'm definately going to try debian and knoppix.  I'm sure they're not going to be as easy to use as ubuntu but I'll deal with what I can get.  Just one thing though, in the ubuntu community docs [https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") it says you can install with the help of floppies (not just floppies, usb also of course) on 5.10, is that wrong?
Thanks,
Kev

---

