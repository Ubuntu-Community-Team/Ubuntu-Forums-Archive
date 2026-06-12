---
title: "Dual booting with 2 drives (New to this)"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by VincentRP on 2007-03-04
Hey,

I've run several different flavors of Linux on my desktop for a while now and have always dual booted, however that system only has one hard drive, so I was just setting up dual boots on seperate partitions.

Now, I have a laptop (Specifically, an HP dv8000t) that has Windows on it.  This notebook has room for an extra hard drive, so I'm putting a second drive in tomorrow when it arrives.  I want to install Ubuntu on that drive.  Now, I'm worried I might have some problems with this, seeing as the BIOS on the HP is so restrictive.  If I install Ubuntu to the new drive and put the bootloader on the MBR, should (in theory) everything work alright?  Or would you (you know, the experts) anticipate any sort of problems?

Thanks much in advance for any help.

---

### Post by bulldog on 2007-03-04
Are you using Sata drives or IDE?
Because if you use Sata you can choose to install GRUB on your new disk and install ubuntu on the same disk.
Then you have to change the boot order in your BIOS to the new drive and you'll be able to start windows and ubuntu from this drive [maybe a little tweaking of the menu.lst is necessary]
Your windows disk stays like it is and if you get troubles with GRUB or ubuntu,you can always boot into windows with it's own bootloader by switching the boot order of your hard disk.

---

### Post by VincentRP on 2007-03-04
Thanks for the information.  Yes, the notebook uses SATA drives, so it sounds like it should be pretty simple to just put it on the Ubuntu drive and set that first in boot order.

Again, thanks :)

---

