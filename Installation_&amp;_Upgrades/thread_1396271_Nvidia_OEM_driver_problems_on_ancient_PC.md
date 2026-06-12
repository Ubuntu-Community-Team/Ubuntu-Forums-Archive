---
title: "Nvidia OEM driver problems on ancient PC"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by hmoulding on 2010-02-01
I've got an eight-year old PC that I'd like to breath some new life into. I was using it for my old scanner (HP, no longer supported by MS or HP), but when my Windows installation finally died I thought it was a perfect time to try Ubuntu. (Xsane running under Ubuntu does support that scanner. Yippee!)

I can get Ubuntu started on it, but when I try to activate/install the recommended Nvidia OEM driver, the system gets sick. Ordinarily I'd not worry about it, but the system only starts into low graphics mode, which leaves some dialogs too large for the display and partially unusable or worse. I'm sure I'm doing something wrong, but I'm a Linux n00b, so I have no idea what I need to do to fix this. 

The PC is a cheap homebrew, using an A7N266-VM ASUS mb. It has some kind of Nvidia chipset on board, but no graphics accelerator. 

Any help is appreciated! 
-- 
Helge

---

### Post by jerrrys on 2010-02-02
have you tried ENVY?  it should find the proper driver for you.  it can be found in the Software Center.

---

### Post by hmoulding on 2010-02-02
> **jerrrys said:**
> have you tried ENVY?  it should find the proper driver for you.  it can be found in the Software Center.

I hadn't tried it before, but once you provided the pointer, I tried it. It indicated one possible driver to be compatible, so I activated that.

But the result is the same as before. A pretty much unusable system, with a terminal login prompt flashing on the screen. It's unusable because apparently it doesn't pick up keystrokes, either, only sometimes. So I can type in my user name, but typing in the password is not possible because I can't tell which of my keystrokes take without the echo.

Plus, for some reason it won't boot into grub, now, so I can't even select the recovery mode. Is it possible to fix that without doing another clean install?

Otherwise I guess I need to do another clean install and try something other than ENVY.
-- 
Helge

---

