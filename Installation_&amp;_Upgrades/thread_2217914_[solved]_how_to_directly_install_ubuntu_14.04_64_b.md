---
title: "[solved] how to directly install ubuntu 14.04 64 bit from iso image file?"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by shayli147 on 2014-04-18
Hello there,

Some general details to start with- I am not that new into Ubuntu, have been using it since 9.04 32 bit so the Terminal is a friend (somehow).
By that time this PC had 1 GB RAM and couldn't handle 64-bit also there was no need to.
Lately I have been using painting and edditing softwares for a living and had to support my PC with some more RAM and now, as I use it with 4 GB RAM I thought it would be even more fun to use my buddy even faster so 64-bit came to my mind.

So the  thing is that the automatic installation of the system from 12.04 to  14.04 was 32-bit.
My computer has been formatted and it's completely  empty so I don't have the problem of losing files.
For the last two days I have repeatedly searched the web on how to install 64 bit, found that _my processor  can accommodate it_, and downloaded the .iso file.
I can  not burn the file to a disk or move it to a USB device and when I tried to run it  directly, nothing happened. I searched the web for some help on that matter and mainly  found explanations about installing from a DVD or USB and transfering from Windows to Ubuntu which  weren't exactly helpful here.
The most helpful result I found was relevant  to 12.04, _also not to my dist_ and I'm not sure if it's ok to use it on my Ubuntu:
[http://askubuntu.com/questions/340156/install-ubuntu-from-iso-image-directly-from-hard-disk-of-a-system-running-linux](http://askubuntu.com/questions/340156/install-ubuntu-from-iso-image-directly-from-hard-disk-of-a-system-running-linux)

My question to you is if this search result can work -the way it is- on the _Ubuntu 14.04_ I have, and what are the minor changes I need to pay attention to?
Or if there is a better way to do it- since I assume something might have developed through the years. :)

Hope I have included all the needed details.
With great appreciation for helpers,
Shay-li

---

### Post by _duncan_ on 2014-04-18
Method 1: [Boot and Install Ubuntu from the GRUB rescue prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

> I have not tried this method myself, so I can not say for sure if it works or not.
> Assumes you already have GRUB2 in your system from a previous Ubuntu (or similar) installation.
> Looks like it may work on a single drive system.


Method 2: [ISO Booting from GRUB, then Installing from the Running LiveCD]("https://help.ubuntu.com/community/Grub2/ISOBoot")

> This is the method I used to install Precise 12.04 a few years back, and now Trusty 14.04.
> Seems to only work if the system has 2 drives: 1 drive will hold the downloaded ISO while the other drive contains the target partition(s) for installation.
> **I have never been able to make this work on a single drive system**. I can boot the ISO image just fine with 1 drive, but the installer will insist on unmounting the loopback device during installation.

---

### Post by squakie on 2014-04-18
Why can't you burn the ISO (it takes a DVD r/w drive and disk)?  Also, may seem like a dumb question, but are you trying to ask how to update your 32-bit 14.04 to 64-bit 14.04?  If so, I *think* the only true way is to back up what you need, then re-do an installation of 64-bit from scratch.  I'm sure someone will comment on that if I'm wrong.

---

### Post by shayli147 on 2014-04-19
_duncan_ - Thank you! I only had to play abit to find the grub location, other than that it took a while but all went smoothly :)

squakie - This is exactly what I wanted to do, my question was for the right way to do it from the inside since my DVD r/w drive needs to be fixed.

---

