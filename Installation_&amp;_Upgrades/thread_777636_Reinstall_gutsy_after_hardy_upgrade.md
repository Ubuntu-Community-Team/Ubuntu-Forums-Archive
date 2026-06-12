---
title: "Reinstall gutsy after hardy upgrade?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by lian1238 on 2008-05-01
Hi everyone!

I would like to know what's the best way to downgrade from Hardy (official release) after an upgrade from the alternate install CD? I want to do a fresh install of Gutsy, but I have my /home + ~/Pictures + ~/Music on 3 other partitions. There is a lot of hidden folders in ~/ so is it safe to just reinstall Gutsy into the root directory, which means the hidden folders will still exist? Or should I delete them first?

If you're wondering why? Because..
There are some things in Hardy which don't work for me..
1. My wireless doesn't detect any networks & no LED
(even on LiveCD and downgrading -- installing network-manager_0.6.6-0ubuntu1_i386.deb -- doesn't work)
2. Many icon themes don't seem to work anymore (even on LiveCD)
3. My usb drive doesn't automount
(haven't tried on LiveCD),
("[sudo modprobe -r ehci_hcd]("https://bugs.launchpad.net/ubuntu/+bug/211760")" and "[lsusb]("http://ubuntuforums.org/showthread.php?t=770391&page=4")" don't work)
(there is no [usefree option]("http://ubuntuforums.org/showthread.php?t=770391&page=3") in gconf -> system > storage > default_options > vfat)

I have given up trying to fix these. I'll wait until Hardy becomes more stable.

---

### Post by Pumalite on 2008-05-01
This might help:
[http://ubuntuforums.org/showthread.php?t=623058](http://ubuntuforums.org/showthread.php?t=623058)

---

