---
title: "xserver is broken in Hoary Install"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by slow'puter on 2005-03-15
I went from Warty to Hoary on my P3 laptop, and now I do not have a functional screen. Let me explain: when gnome is supposed to start, the screen shuts off. The computer keeps on working, the Ubuntu drums for login can be heard, but no display.

I ctrl-alt-backspace several times until a blue screen with some debbuging message came up. It disabled xserver and I was in console mode. I tried dpgk-reconfigure xserver-xfree86 and the following message appeared:

xserver-xfree86 is broken or not fully installed

How do I fix it? Can't install ndiswrapper because I don't have the linux-kernel installed, so I cannot do apt-get.

---

### Post by bored2k on 2005-03-15
[QUOTE=slow'puter]I went from Warty to Hoary on my P3 laptop, and now I do not have a functional screen. Let me explain: when gnome is supposed to start, the screen shuts off. The computer keeps on working, the Ubuntu drums for login can be heard, but no display.

I ctrl-alt-backspace several times until a blue screen with some debbuging message came up. It disabled xserver and I was in console mode. I tried dpgk-reconfigure xserver-xfree86 and the following message appeared:

xserver-xfree86 is broken or not fully installed

How do I fix it? Can't install ndiswrapper because I don't have the linux-kernel installed, so I cannot do apt-get.[/QUOTE]


Hoary does not work with xfree, wors with xorg

try  sudo dpkg-reconfigure xserver-xorg, this fixed things for me.
There are more advanced threads about this, but this is probably the 1st thing you could check.

---

### Post by slow'puter on 2005-03-15
It just shows how much od a n00b I am.

Thanks!

---

