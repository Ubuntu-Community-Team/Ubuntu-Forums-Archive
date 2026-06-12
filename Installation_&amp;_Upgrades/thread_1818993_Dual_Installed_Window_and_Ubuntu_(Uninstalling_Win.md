---
title: "Dual Installed Window and Ubuntu (Uninstalling Windows)"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by SecretSpetsnaz on 2011-08-05
I had Windows 7 as my first OS and Now Im running Ubuntu 11.04 (Natty Narwhal) now i want to Uninstall windows 7 starter (correction) i want to know if this is possible and if so how? also i want to uninstall it because when i boot up windows 7 starter it runs very slow

---

### Post by Blasphemist on 2011-08-05
Please run this boot info script to let us see how your partitions are set up and we can be pretty specific on just what to do. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by x-D on 2011-08-05
You have a couple of options...

First of all, if you don't mind losing all your data, (or if you can back it all up easily), plop your live disk or usb into the computer and chose to install ubuntu by itself, deleting everything else.

For the option where it is easier to keep data, find out which partitions hold Windows 7 things, and using a partition tool (GParted is best) delete and reformat the win7 partitions and then add the space taken back from them into your Ubuntu partition. The one you will want to put the extra space into is the one with all your files and folders in (ie - your videos etc), so find out first... it will PROBABLY be the largest one!

Hope this helped,

x-D

:guitar:

---

