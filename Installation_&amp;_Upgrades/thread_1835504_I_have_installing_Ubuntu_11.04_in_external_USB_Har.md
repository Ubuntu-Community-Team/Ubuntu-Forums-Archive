---
title: "I have installing Ubuntu 11.04 in external USB HardDisk in one laptop with &quot;wubi&quot;..."
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-08-29
hello, 
apology from my English...
I have installing Ubuntu 11.04 in external USB HardDisk in one laptop with "wubi"...
how can I boot with this external USB HardDisk in another laptop without installing again?
I wait for your answer...
thanks a lot...

---

### Post by Mark Phelps on 2011-08-29
I don't think you can do that.

It's like asking how can I use a Windows app installed on one PC on a different PC -- you can't, you have to install it again.

Wubi installs Ubuntu in the same manner as Windows apps; thus, while the file (root.disk) exists on the external drive, all the info needed to access the file exists on the internal drive of the original PC.

You could probably do what you want by installing Ubuntu to an external drive, but NOT using Wubi.

---

### Post by bcbc on 2011-08-29
This talks about how wubi boots and how you would go about copying it between machines.
[http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines](http://askubuntu.com/questions/56726/can-i-copy-my-wubi-install-between-machines)

In your case, you want to just boot an existing wubi install from the external. In that case, you'd just need to copy \ubuntu\winboot\wubildr to C:\wubildr and then [add an entry to the bcd]("http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/"). If you're using XP (not Win7/vista) it's a little different.

But if you want to use the same external on both computers (switching between) you'll have issues if the partition is seen differently. If it's all UUID based you're okay, but depending on the release, the partition is hardcoded in the grub.cfg.

Personally... if you have an external drive, it's better to install directly to it, then you can boot from the external more easily as mentioned by Mark Phelps. And note that it's possible to [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") a wubi install from just the root.disk to a different computer (assuming no custom drivers that are present on one computer and not the other).

---

