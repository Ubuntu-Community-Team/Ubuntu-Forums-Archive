---
title: "Ubuntu server (lts) with Sapphire edge HD"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by thomasliveqube on 2011-04-26
I'm having problems getting Ubuntu 32bit server 10.04 working with the Edge HD. From what I've read in reviews and forums, Ubuntu is supposed to work fine with this hardware. Though it might be a different story when it comes to the server version, which I haven't found any articles on.
It seems to install properly, but it will not boot from the hard drive - only from flash. We have of course set the hard drive as priority for booting. All that happens is Bios check, and then the underscore remains blinking in the top left corner.

Ideas anyone?

---

### Post by unisubzero on 2011-07-05
Maybe a bit to late but ...

The problem is that you installed grub on the flash driver instead of your HDD.
When you get the question where do you want to install grub chose manual select (or something like that) and type /dev/sd* (ex. /dev/sdb) sd* is your HDD.

You can also fix it by booting your PC with flash drive plugged in and then reinstall grub.
Check grub HowTo install/reinstall.

---

