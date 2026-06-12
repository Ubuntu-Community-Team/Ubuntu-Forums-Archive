---
title: "Problem installing on 64bit + x800xl"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by infused on 2006-06-09
Hi guys,

I am a linux newb. I have the 6.06 release. It boots off cd fine. Normal installtion seems to work ok until it has finished mounting everything etc, screen goes black then I get alot of errors about XServer and I/O errors.

There is nothing wrong with the hard drives or anything and from what I can tell it seems to be a problem with the x800 ATi card.

If I select safe graphics mode after everything has mounted etc the screen goes blank and my LCD says no signal. Nothing responds, not even the cdrom will eject.

I can try get the error codes.

Sepcs:
3800 Dual Core
1gb Memory
X800XL
Audigy 2 ZS

---

### Post by infused on 2006-06-09
Errors:

Failed to Start X Server

WE: Driver using old /proc/wireless Support
Buffer I/O Error on device sdb1

---

### Post by infused on 2006-06-10
Ok, after doing: sudo dpkg-reconfigure xserver-xorg I have set everything up but how do I restart the installtaion?

---

### Post by infused on 2006-06-10
I really need help with this. I cannot find information anywhere to solve my problem.

---

### Post by -::Bas::- on 2006-06-23
Hi Mate,

Don't know if u 've solved the prob already, but if you didn't: check Louis' solution [http://www.ubuntuforums.org/showthread.php?t=200559](http://www.ubuntuforums.org/showthread.php?t=200559)
It might help you.
Good luck!

---

