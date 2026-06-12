---
title: "Installing to a seperate hard drive?"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by hotroddude on 2007-11-09
First off im extreamly new to linux, and cant manage to make my live cd to work ( cant get my BIOS to open up either ) I have two hard drives in my computer,so  is there a way to install gutsy gibbon onto my empty hard drive withought a live disk?

thanks in advance,
steven

---

### Post by Steven_B on 2007-11-09
You have a few options, depending on what the problem is:
-If you have a floppy drive, you can install [Smart Boot Manager]("http://sourceforge.net/projects/btmgr/") onto it and use it to boot a CD.
-If the LiveCD is crashing or otherwise not working, you can use the Alternate Install CD.  You will still need to be able to boot from a CD to do this, however.
-Install [Wubi]("http://www.wubi-installer.org") from within Windows.  From Wubi, you can re-partition your disk(s) and move the Wubi installation to it's own partition.

---

### Post by hotroddude on 2007-11-09
thank you very much for the wubi link, im download it now :) hope this works
thanks again,

steven

---

### Post by hotroddude on 2007-11-09
hmm i have a new problem here lol, when it asks me what OS i want to use my keyboard stops working ( it is not wireless ) any idea what could be causing this?

---

### Post by Steven_B on 2007-11-09
Is it USB?  This might be of use:
[http://www.linuxforums.org/forum/installation/31216-boot-loader-problems-usb-keyboard-doesnt-work.html]("http://www.linuxforums.org/forum/installation/31216-boot-loader-problems-usb-keyboard-doesnt-work.html")

---

### Post by hotroddude on 2007-11-09
thank you so much! im runing feisty right now.
thanks a ton,
steven

---

