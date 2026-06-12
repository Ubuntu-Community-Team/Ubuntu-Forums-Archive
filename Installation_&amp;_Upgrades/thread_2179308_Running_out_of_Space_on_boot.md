---
title: "Running out of Space on /boot"
date: 2013-10-07
forum: Installation &amp; Upgrades
---

### Post by JDuchows on 2013-10-07
I am quite a bit of a newbie at this and I've installed my first version with 12.04 64-bit and been upgrading it ever since. I just followed all defaults but now have run into this problem - I can't install the latest upgrade (been doing with with apt-get update; apt-get upgrade and apt-get dist-upgrade, then following with clean, autoclean and autoremove, but finally I've run into the point when the installer keeps only complaining about insufficient space on /boot. I looked at it with GParted but there doesn't seem to be a way to resize the current partitions without killing the entire OS. I've uploaded both the GParted and the /boot images and if someone could please help me out of this mess, I would be most appreciative. Thanks!

Best Regards, John

---

### Post by oldfred on 2013-10-07
I do not know LVM, but with the separate /boot you should periodically houseclean kernels. They are not automatically removed.

I prefer to use synaptic but you can use command line. I normally keep current and one older one just in case.
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones

Also command line in post #8 - example below is 3.5 generic, use your version.
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

