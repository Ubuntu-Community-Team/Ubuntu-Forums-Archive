---
title: "Fresh Install of 7.10 on ITE8212 Raid 0+1"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Mrlush123 on 2008-02-06
I am trying to Install 7.10 on a Raid 0+1 ITE 8212 contoller. When I go to install the disks are not there. How can i get it to recognizes the Raid configuration?

---

### Post by Afflictedmonkey on 2008-02-12
**Short Answer:**
You can't

**Long Answer:**
You will need to recompile the kernel with the experimental pata_ITE8212 driver switched off and the old 8212 module activated instead. This causes lots of other problems and breaks forward compatability (means you cannot upgrade to next ubuntu release, you will have to do a fresh install), it also breaks your video card install (easily fixable with Envy for nVidia) and the restricted driver manager may also be broken, also it is not particularly trivial to do!

Here are a few other links on the 8212 problem:
[http://ubuntuforums.org/showthread.php?t=107183&highlight=ITE+8212](http://ubuntuforums.org/showthread.php?t=107183&highlight=ITE+8212) 
[http://ubuntuforums.org/showthread.php?t=11195&highlight=ITE+8212](http://ubuntuforums.org/showthread.php?t=11195&highlight=ITE+8212)

I got it to work by following the instructions here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I think this is a better howto:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

then using the 'make menuconfig' program to activate the IT8212 module (it's in drivers somwehere). Remember to deactivate the pata_IT8212 driver.

---

