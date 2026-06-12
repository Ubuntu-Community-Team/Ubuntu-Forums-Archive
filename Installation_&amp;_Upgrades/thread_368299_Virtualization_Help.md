---
title: "Virtualization Help"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by hipnerd on 2007-02-23
I am considering buying a new machine to help move me father down the path towards the total elimination of Windows. I am currently dual-booting Ubuntu and Windows XP Pro. I'd like to charge that so that I am only booting Ubuntu and I use virtualization to call up an XP desktop when I need it.

I've read tons of threads on this subject. And it is not clear to me that this technology is mature. Major problems seem common, and hardware support is spotty.

I am probably going to build a new box for this project, and I want to give myself the best chance for success. 

What CPU should I choose? I was leaning towards an AMD64 x2 for price reasons, but it seems that AMD54 x2 CPUs don't like Xen. Is a Core2Duo my only real choice if I want SMP with hardware virtualization?

Any other hardware I need to avoid? Video cards?

What virtualization package will give me the best chance for success? I've seen:

Xen
VMware
Parallels
KVM
QEMU
etc.

I'd like to have Windows run as fast as possible of course. But I'd also just like the thing to work. I wanted to see if anyone had any opinions on this before I went out and spent money on a new box.

Thanks for your time.

---

### Post by trimtab on 2007-02-23
I have found that VMWare works best for virtualizing Windows at this moment. However, your dependencies are not stated. You will find that while all the basics (ethernet, disk, cd-rom) work fine when you start using things like USB or expect some hardware (you will not see that expensive video card) to be visible in the virtualized environment you will be disappointed. Virtualization by definition means isolating the virtualized environment from hardware.

Here are instructions on installing VMWare server on Ubuntu:

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

There is also the option of moving/converting an existing Windows system into a VMWare image:

[http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

The process is simply enough that you should try it and see if it meets your needs. YMMV.

---

### Post by hipnerd on 2007-02-23
Fair enough advice. The second part of my question involved hardware. An AMD 64-x2 CPU appealed to me for budgetary reasons, but I have seen many threads where people appeared to have problems with this technology and AMD's dual-core CPUs.

Have those issues been resolved? Or do I need to go to Intel in order to have this work?

---

