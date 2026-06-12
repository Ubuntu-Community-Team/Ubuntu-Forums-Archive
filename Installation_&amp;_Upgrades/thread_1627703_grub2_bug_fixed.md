---
title: "grub2 bug fixed?"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by koenfloris on 2010-11-21
hi.

my girlfriend screwed up her vista-computer, now she ask me to put linux on it.

she doesn't know anything about computers. and she uses some hardware i suspect Ubuntu will have trouble with.

so i will put windows on it, and an wubi-install Ubuntu.

now i am asking you guys, i remember wubi having trouble with grub2, is it fixed?

is it already possible to move from wubi to a partitioned installation? in case she likes Ubuntu, i need to make it permanent.

thx in advance!

---

### Post by bcbc on 2010-11-21
Wubi has issues with grub2.

1. If you install to a different partition than windows, it prompts you during grub updates to install the grub bootloader to the drive MBR. If you choose to do so, it will overwrite the windows bootloader and prevent either OS from booting. Fix is easy enough. Problem can be prevented by not checking any of the devices listed.

2. Lately updating grub to new releases can introduce inconsistencies between the wubildr file and the grub modules?? (not entirely sure where the problem lies). Basically grub will update the wubildr file, but then it still doesn't understand the new commands in grub.cfg. The resulting symptoms are either 1) messages followed the grub menu, and then normal booting, 2) grub prompt without a menu or 3)straight reboot

My advice is that if you choose to use wubi, go into Synaptic and lock the versions of grub-pc and grub-common and possibly lupin-support. Most grub updates are not security updates - are unnecessary, and lately, yes, break wubi installs.

3. You can migrate a wubi install with this guide: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
You need to manually create the partitions before migrating.

---

