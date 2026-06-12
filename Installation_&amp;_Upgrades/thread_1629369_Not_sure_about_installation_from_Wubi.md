---
title: "Not sure about installation from Wubi"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by knightwriter on 2010-11-23
I am a new user and love Ubuntu. I have it on my hp pavilion vista 32 bit with wubi. I have everything that I want back up on an external hard drive from vista. I would like to make ubuntu my sole os. I'm not sure how to go about this other than downloading the iso to my external hard drive and then installing from there. I have a couple of questions about this.

1. If I do an installation from my hard drive, will it wipe out all the emails and settings that I've already made with wubi?
2. Is there an easier way to get my machine running ubuntu only?

Thanks in advance for all the help and suggestions.

---

### Post by Frogs Hair on 2010-11-23
Your Ubuntu partition currently resides in windows ,(this is what Wubi does) so if you remove windows you remove ubuntu.

If you have an option to make a live cd it is a good thing to have around and a fresh install on a clean hard-drive would a good place to start.

---

### Post by davidmohammed on 2010-11-23
welcome aboard!

whilst it is possible (just) to backup your various email and other settings that you've made in your wubi install following by reapplying onto a fresh ubuntu install - it can be very tricky and error prone.  One for those feeling particularly brave.

Personally, I would burn a CD containing ubuntu.  Use add-remove programs to delete your wubi install.  Then install ubuntu by booting from the CD.  During the boot screens you will be offered whether to install side-by-side with windows, or just erasing your entire disk and installing ubuntu.

Once done, re-do your customisation by hand such as email, graphics etc.

---

### Post by knightwriter on 2010-11-23
Ok. Thanks for the help. I don't happen to have any cd's, but I do have an external hard drive with close to 100 gig on it still. Can I download it to that and then do a fresh/clean install?

---

### Post by davidmohammed on 2010-11-23
making the assumption that an external hard-drive install is very similar to an usb stick install... (never done this myself!) -you could try [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick") to do the installation.

---

### Post by oldfred on 2010-11-23
See these instructions:

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by bcbc on 2010-11-23
Uninstalling Ubuntu from add/remove programs will delete all your data on wubi. You can backup your /home directory and restore it later if you want to keep everything, or just save the root.disk and copy stuff over later.

I wrote a guide to migrate wubi installs to partition. You can use it to keep all your settings and data. You just need to create the partitions first. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Edit: you beat me to it, oldfred ;)

PS:
From vista (assuming you don't have 4 primary partitions) you could use the Vista disk utility to shrink the windows partition. Then boot wubi and use Gparted to create a new extended partition, and inside that 2 logicals, one for root and the other for swap. Then migrate wubi to that.
After that you can format and reuse the windows partition as data or use it as a separate home...

---

### Post by knightwriter on 2010-11-23
Ok. I've downloaded the iso for unbuntu 10.10 to my external hard drive. Then I go to system>admin>start up disc creator. I find the cd information on my external hard drive and then use my external hard drive to create the start up disks but it gives me an error stating:

Installation failed. Failed to install the boot loader.

Any suggestions?

---

### Post by wilee-nilee on 2010-11-23
> **knightwriter said:**
> Ok. I've downloaded the iso for unbuntu 10.10 to my external hard drive. Then I go to system>admin>start up disc creator. I find the cd information on my external hard drive and then use my external hard drive to create the start up disks but it gives me an error stating:

Installation failed. Failed to install the boot loader.

Any suggestions?

Yeah look at the last two posts before yours # 7 & 6. Also tell us where your at you can transfer that wubi to a partition. You can also keep the Vista if you want.

As far as using the startup disc creator it is for loading a thumb basically. It could be used for a external HD but it is only the ISO put to a partition, with persistent if you want it. It is problematic as far as updating kernels, it is not a regular install, it's for loading a thumb to install with mostly.

And before the disc creator users come out of the woodwork to argue their points I know all its uses.

---

### Post by oldfred on 2010-11-23
Are you trying to directly boot the ISO from the hard drive. If so you need to install grub2 to a partition that you create for the install and loop mount (somewhat like wubi does) the ISO to load it.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

I prefer to use USB Flash drives if your system can boot a flash drive. It is reusable and can even hold more than one ISO if large enough.

---

