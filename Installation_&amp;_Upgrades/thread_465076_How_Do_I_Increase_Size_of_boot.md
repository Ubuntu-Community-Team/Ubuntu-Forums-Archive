---
title: "How Do I Increase Size of /boot?"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by bper on 2007-06-05
Hi,

I have a 25 MB /boot partition on a machine running feisty. I see that my boot partition is used 98%. I thought 25 MB would be enough. Is it possible to increase the size? Or are there things that should be removed? I've installed gparted, but I can't unmount the boot partition and don't know how to do it manually. I can't even increase the size of another partition in gparted that I have unmounted. When I try to apply the resize, gparted tells me that the partition is mounted.

If you can help me, I'd appreciate it.

Thanks

---

### Post by taurus on 2007-06-05
You need to use the LiveCD to resize Ubuntu since you cannot use it and resize it at the same time.  However, I recommend you use GParted LiveCD since it comes with the latest version of gparted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by bper on 2007-06-06
Thanks for your help.

I have gparted livecd but I still can't resize /boot.

Again, /boot is a 25 MB primary partition followed by extended partitions followed by about 40 GB of unused space.

I haven't been able to resize the boot partition at all. gparted won't let me increase it, add any partitions or free  space after /boot.

How can I resize it? Am I doing something wrong, or is /boot or extended partitions special cases?

Thanks.

---

