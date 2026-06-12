---
title: "Weird Grub stuff after install &amp; upgrade"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Daveydave2 on 2010-02-06
Hey gang, I just installed 9.10 and partitioned my drive with my exsisting Windows 7 install. Anyway, everything went fine, then I went to see what updates there were. As it was installing the updates, it asked if I either wanted to replace GRUB with the new one or not, plus another option. I think I had it replace, but now when I boot up there are two Ubuntu images (one with a new version number than the other). I have been picking the newer version and all seems well. Did I screw something up? Is there a way (other than just editing the grub file) to "uninstall" the other partition?

---

### Post by coldfusion1313 on 2010-02-06
No, you did not do anything wrong, it is just an annoy thing of GRUB. :)

---

### Post by presence1960 on 2010-02-06
> **Daveydave2 said:**
> Hey gang, I just installed 9.10 and partitioned my drive with my exsisting Windows 7 install. Anyway, everything went fine, then I went to see what updates there were. As it was installing the updates, it asked if I either wanted to replace GRUB with the new one or not, plus another option. I think I had it replace, but now when I boot up there are two Ubuntu images (one with a new version number than the other). I have been picking the newer version and all seems well. Did I screw something up? Is there a way (other than just editing the grub file) to "uninstall" the other partition?

**_*That is not an annoying thing of GRUB.*_** You upgraded to a newer kernel and that is why you have 2 Ubuntu kernel choices in the GRUB menu. It is a wise thing to keep 2 kernels installed on your machine in case the newest one borks you can boot into the next newest kernel. 

On the next kernel upgrade it would be OK to uninstall & remove the oldest kernel from Synaptic Package Manager. To uninstall a kernel and have it's package removed from cache in Synaptic mark for Complete Removal the following:

For kernel 2.6.32-11 remove

* linux-headers-2.6.32-11
* linux-image-2.6.32-11
* any entry above followed by -generic 

This will uninstall that kernel and remove it from cache on your ubuntu. They should be removed from your grub menu.

---

