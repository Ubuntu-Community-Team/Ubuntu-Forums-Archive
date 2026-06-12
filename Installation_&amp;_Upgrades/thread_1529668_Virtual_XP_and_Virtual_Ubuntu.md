---
title: "Virtual XP and Virtual Ubuntu"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by ericwright17 on 2010-07-12
I'm not sure if what I want to do is possible, but I believe that it should be.

I've been running Ubuntu for several years and I love it, however, I still run XP in VirtualBox, because OpenOffice does not do what I need it to and I need my good ole M$ Office.

However, when I restart my Ubuntu system, the XP needs to be put on hold too.  Also, XP never gets the performance I need, for example if I want to edit video, I can't.

So is it possible to get a little linux system running, and then get Ubuntu and XP running virtually on top of that OS?  I could then restart the machines independently and even pause one if the other needs more resources?

One final question, is there a way to slim down Ubuntu so that it only loads drivers needed by VirtualBox.  I mean that the virtual hardware will never change, so can we optimize Ubuntu for that hardware???

---

### Post by chessnerd on 2010-07-12
A dual-boot would be a much better option for you. This kind of a setup will only result in poorer performance from both of the virtual OSs.

Virtualization technology is still pretty new, and unless your computer has built-in hardware-level virtualization capabilities there is little you can do to "optimize" a system for virtualization.

---

### Post by ericwright17 on 2010-07-12
Thanks for your reply, fellow Michigander!

I've dual-booted before, and that doesn't do what I need either...

My computer uses AMD's Hyper-V to assist in hardware virtualization.

---

### Post by chessnerd on 2010-07-12
Okay, then if you are looking for a minimalist distro for this then I would probably suggest Debian Lenny with Openbox. It will be light and should be quite stable.

Other options would be:

Arch, Crunchbang, X/Lubuntu, Puppy, Slitaz, TinyCore

I'm not sure about how you might optimize it for virtualization, but there is a post about it on this forum: [http://ubuntuforums.org/showthread.php?p=7300082](http://ubuntuforums.org/showthread.php?p=7300082) and Google might be able to help you there: [http://www.google.com/search?hl=en&q=optimize+virtualbox+ubuntu&aq=8&aqi=g9&aql=&oq=optimize+virtual&gs_rfai=](http://www.google.com/search?hl=en&q=optimize+virtualbox+ubuntu&aq=8&aqi=g9&aql=&oq=optimize+virtual&gs_rfai=)

Also, you a U of M or State fan?

---

