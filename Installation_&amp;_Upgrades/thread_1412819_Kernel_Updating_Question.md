---
title: "Kernel Updating Question???"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by HeatR216 on 2010-02-21
Whenever I update my kernel through the ubuntu Update manager, my grub gets reconfigured and shows ever kernel version I have ever updated to. So far on Ubuntu 9.10, my grub shows updates from 2.6.31-14 to 2.6.31-20. Does this mean that I have all those kernels on disk? or has the kernel just been overwritten and the other kernels listed are just because grub has been added too? 

Also on a side note. Everytime I upgrade, as mentioned above, my grub updates and removes all my changes. I normally like to rename the kernels of ubuntu to something better, rename my windows 7 partition so it looks nicer and I usually change the resolution so its not 640x480 (I like 1680x1050 which is what my laptop uses). Is there anyway to permanently keep these changes minus the kernel updating stuff? Like to keep my grub the same?

---

### Post by lidex on 2010-02-21
Karmic uses grub2 which is edited differently than legacy grub.
> #
grub.cfg is overwritten anytime there is a update, a kernel is added/removed, or the user runs update-grub
#
The user can use a custom file, /etc/grub.d/40_custom, in which the user can place his own entries. This file will not be overwritten. 
was taken from this page:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")
Go there for detailed info. The old kernels remain unless you specifically remove them. I usually keep the latest two in case I need to fallback. Synaptic is one way to remove them although ubunutu-tweak makes it pretty easy.

---

### Post by presence1960 on 2010-02-21
you can uninstall and remove the kernels you do not want from Synaptic Package Manager. Mark for Complete Removal:

linux-headers-2.6.31-xx
linux-image-2.6.31-xx

This will uninstall them and remove them from cache on your system. They will be gone and any further grub updates will not find them. Please note it is not mandatory but wise to keep the two newest kernels so if the newer one borks you can boot into the next most recent kernel to troubleshoot.

---

