---
title: "packages linux and linux image - what is the difference?"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by sup on 2006-07-11
I read on the web that for still fairly new processors like mine (Pentium M 1.7) is better linux kernel optimized for them, i.e. linux-image-686.

 So I went to synaptic, searched for 686 and isntalled it.  I did not uninstall the old 386 package and today, when a new kernel appeared in the depositories, I had to download almost 100MB and when I rebooted, grub menu had at least 10 items in it. So I went to synaptic again with intention of uninstallin some unecessary kernels (I do not have that much space on my 5GB root partition anyway, just about 1GB available) and noticed that there are packages namend "linux-386, linux, linux-686" and then named "linux-image-386" "linux-image" etc. What is the difference?

And by the way, I knowit is good to keep some old kernels in case the new one does not work properly, but it does not mean I need to keep all the kernels, right, especially when the last then-new to-be-replaced kernel showed to be stable, right?

---

### Post by nkhansen on 2006-07-11
linux-image-686 is a dummy package pointing to the latest version of the kernel image optimized for i686

linux-686 is a dummy package pointing to the following dummy packages:
linux-image-686
linux-restricted-modules-686

In this way all you have to do to install a complete kernel including restricted modules is to install the linux-{arch} dummy package, and all needed packages will be added automagically.

To remove linux-386, you should remove the specific package:
linux-image-2.6.15-25-386

All other things will then be removed as well.

I think that if you use aptitude to install stuff (and hopefully a future version of synaptic), you should be able to remove linux-386, and all things installed as dependencies will be removed at once.

---

### Post by sup on 2006-07-11
thanks a lot, it clarifies it very nicely.

---

