---
title: "Grub delete windows in menu.lst when kernel updates"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by romaluca on 2007-04-27
Grub delete windows in menu.lst when kernel updates and i must to insert it every time.

Is possible tell grub, not remove windows from file menu.lst?
Thanks

---

### Post by Herman on 2007-04-27
Hello romaluca
Yes, it's easy to do that, just refrain from placing your Window boot entries inside the debian automagic kernels area and that won't happen anymore. :)

There are signs in UPPER CASE characters marking both the beginning and the end of the debian automagic kernels list. 
They are the only lines in UPPER CASE in the whole menu.lst file, so they are easy to see. 
We can place other operating system entries either above or below that area.
We are not supposed to put anything in that area that doesn't belong to the operating system that owns the file. The contents of that area are subject to change by the update-grub script that runs each time Ubuntu receives a new kernel. 
```
[### BEGIN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST")
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
``` Don't put your Windows entry anywhere in this part of your menu.lst file and it will be okay. ```
[### END DEBIAN AUTOMAGIC KERNELS LIST]("http://users.bigpond.net.au/hermanzone/p15.htm#DEBIAN_AUTOMAGIC_KERNELS_LIST")

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
```Regards, Herman :)

---

