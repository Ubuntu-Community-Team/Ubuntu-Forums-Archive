---
title: "When Linux starts monitor dims (Power Saving Mode)"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by Broker on 2011-01-02
Hello Everyone,

I have a problem when try to start Ubuntu Linux 10.04.1.
On my PC, i have a dual boot, Windows 7 64-bit and Ubuntu Linux 10.04.1 64-bit. When selecting Linux on Grub, (see picture) [http://img404.imageshack.us/img404/742/img6699x.jpg](http://img404.imageshack.us/img404/742/img6699x.jpg)
afther a few seconds, my the monitor (system?) get in power safe mode.
[http://img600.imageshack.us/img600/6751/img6703.jpg](http://img600.imageshack.us/img600/6751/img6703.jpg)


I had issue during installation 10.04.01, witch i solve like this:

1. Press F6 to open the other menu options.
2. This opens this new menu ... it's useless to us. So now close it!
3. We did this so that the command options show up near the bottom of the screen. Press tab to access these options.
4. Press space ones (to make some space) and enter the following:-xforcevesa
5. Press enter to boot
Source: [http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/](http://www.piotrkrzyzek.com/enter-safe-graphics-mode-in-ubuntu-or-kubuntu-10-04-lucid-lynx-live-cd/)

PS specification:
graphics card is NVIDIA GeForce 9600 GT
monitor LG W2242 (Analog) type 22 "LCD (WSXGA +)
resolution 1680 x 1050.

How to solve the problem?


Note:
Beginner in the Linux world, and my English is very bad.

---

### Post by dli8ilb on 2011-07-16
i just had the same problem as you described, it turned out to be a loose monitor cable.  if that's not the case for you, possibly the video card is dying.

---

### Post by Broker on 2011-08-23
I forgot on this topic.
Ketch was the DVI connector. 
I bought a DVI connector.
DVI to put VGA connector port and problem is resolved. :cool:

Thanks a lot.

---

