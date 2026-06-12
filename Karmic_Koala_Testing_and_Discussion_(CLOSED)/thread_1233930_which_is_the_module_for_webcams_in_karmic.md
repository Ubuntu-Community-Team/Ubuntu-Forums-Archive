---
title: "which is the module for webcams in karmic?"
date: 2009-08-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chriskin on 2009-08-07
i got to know that karmic has full support for my webcam (i use a fujitsu siemens amilo xi 2428 laptop) and i would like to gain that support without going to karmic yet (i'd like to wait for it to hit alpha6 first)

can you tell me which module (or app?library? i don't know) is used in karmic and whether i can get it to work on jaunty as well?
:popcorn:

---

### Post by martinbaselier on 2009-08-07
It depends on your hardware, which kernel module you need. You can install just the new kernel. You can download it here:

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-5-generic](http://packages.ubuntu.com/karmic/linux-image-2.6.31-5-generic)

After you've installed it, it will become your standard kernel. If you have problems because of it, press esc while booting and choose your old kernel (2.6.28-14 is the current one). Then edit your grub menu.

sudo gedit /boot/grub/menu.lst
and change default=0 to default=3
This will make your old kernel the default one again.

---

### Post by chriskin on 2009-08-07
thanks, i'll try it tonight

---

