---
title: "A couple issues on a Macbook"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Spartan22x on 2008-10-23
Hi, I'm having a few issues running 8.10 on my Macbook.

First, and most importantly, I can't find/get synaptics drivers to install. Well, when I installed them, it removed my linux-header package.And it still didn't work. I added the synaptics section to xorg.conf, but it didn't do anything. Also, when I checked with aptitude, it still said I had the linux-headers installed, so I don't know what's up with that.

Edit: in fact, there was NO input device drivers in xorg.conf on my install. I manually added the synaptics section and it didn't do anything.

Also, less importantly, compitz keeps crashing on startup.I don't know what's going on here though.

Any help would be appriciated.

Edit 2: Also, I noticed that sound coming from my speakers is VERY low. It's hard to hear even with max volume. Is there something I can do about this?

Ok, I just realized that a big selling point for the newest version of Xorg is the lack of a config file. So, how are you supposed to change your options? I'd like to enable two finger scrolling on my touchpad, but I don't know how to. Also, I'd like to enable right and middle clicking on it, since I don't have a right mouse button.

---

### Post by wgrant on 2008-10-24
It would help if you used more descriptive titles - I very nearly missed this one.

It's quite intentional that there are no InputDevice sections in xorg.conf - they're largely replaced by HAL-based autodetection. What gives you the idea that you need one? As long as you have xserver-xorg-input-synaptics installed, it should be automatically selected.

---

### Post by wgrant on 2008-10-24
Ah, I see you hid some realisations in an edit...

[The X config docs](https://wiki.ubuntu.com/X/Config#Dynamic%20Input%20Configuration%20with%20xinput) show how to set options at runtime and persistently. Basic options can be set in System->Preferences->Mouse->Touchpad, but that will be more extensive in Jaunty.

---

