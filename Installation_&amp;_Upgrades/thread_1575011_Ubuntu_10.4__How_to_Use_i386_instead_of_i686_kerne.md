---
title: "Ubuntu 10.4 : How to Use i386 instead of i686 kernel"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by arkangel on 2010-09-15
Hi 

I just upgraded my box to  ubuntu 10.4 from 8.04, as usual fast and without complications. 

I want to use the i386 kernel  instead of the i686 (2.6.32-24) with aptitude and synaptics I have downloaded and installed  but  when I restart it jumps directly to  gdm, no grub  to choose,  

I also try to unistall the i686 version trough synaptics, as I did  in previous versions ,  but I couldnt  find any linux-i686 entry 

Any idea ?

Thanks

---

### Post by dino99 on 2010-09-15
i686 is named amd64, so i386=32 bits and amd64=64 bits

with synaptic install pae kernel to use full ram (>= 4 go) instead of the default generic

by default, grub2 menu is not shown if you run only one distro, to see it, either tweak /etc/default/grub or hold "shift" key down at end of bios process

---

### Post by efflandt on 2010-09-15
i686 is not AMD64.  AMD64 is 64-bit x86 (AMD or Intel) and i686 or lower are 32-bit.  For example when I tried to boot 64-bit Ubuntu on my older Pentium w/hyperthreading at work, it refused to run (said I was trying to run 64-bit on i686).

I didn't know there were different 32-bit kernel versions other than an alternate version with PAE for larger memory support.

To see which kernel you are running see the output of **uname -a**

---

### Post by coffeecat on 2010-09-15
> **arkangel said:**
> I also try to unistall the i686 version trough synaptics, as I did  in previous versions ,  but I couldnt  find any linux-i686 entry 


You won't. The generic kernel that comes with 10.04 can run both  64-bit and 32-bit systems. When running 64-bit you'll see x86_64 in the output of uname -a and for 32-bit systems you'll see i686. Why do you want i386? i386 processors date back to the 1980s. If you have a processor unable to run i686 code it probably belongs in a museum.

---

