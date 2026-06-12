---
title: "Install to an eSATA external drive"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by reiki on 2010-03-19
If I wanted to install Ubuntu to an external eSATA drive, how would I do that and not screw up the GRUB install on my primary internal drive? 

I'm guessing I would want to tell that eSATA installation to install its GRUB to the first partition on that drive rather than on my primary internal, but then.... how would I get there from the GRUB on my primary drive?

I guess my problem is that the eSATA drive is not always powered up, and I'm not sure what GRUB (on the primary internal drive) would do if there was an entry pointing to a drive that wasn't there (because it's not turned on)

So what would be the best way to do this?

---

### Post by sebastianabate on 2010-03-19
Install Ubuntu on the eSATA disk, and select your eSATA MBR as target for GRUB (this way you can boot from the disk when is attached to any computer, not only yours).

Then boot your PC from the internal disk with the eSATA disk connected, and run

sudo update-grub

this command detects all the OSs installed on all the disks that your computer have, and makes a menu for each in grub (this include all Linux distributions, Windows, OSX, Solaris, etc.)

When you boot your PC from your local disk, with your eSATA disk connected, you can select its menu item in grub, and the system boots from it, and if you boot your PC without the eSATA disk, don't select its menu (if you selects its menu without the disk connected, you are going to get an error message, and the system must be rebooted)

---

