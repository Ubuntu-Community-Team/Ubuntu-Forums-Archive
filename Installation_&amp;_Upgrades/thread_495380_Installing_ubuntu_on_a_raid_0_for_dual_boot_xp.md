---
title: "Installing ubuntu on a raid 0 for dual boot xp"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by TourTeX on 2007-07-08
Hello everyone, this is my first post and i hope this hasnt already been answered i searched and didnt see anything so. here we go. i downloaded 7.0.4 amd x64 and i am currently running windows xp on a 250x2 raid0 i would like to setup ubuntu and windows xp to dualboot on this raid0 setup. i booted into ubuntu and was fooling around in it and decided i'd try to install it, all went well until i got to the part where you choose to install to (sorry i forgot exactly what the step was called) but it had bolth of my harddrives listed and no options to create a partition or anything like that. i didnt want to mess anything up with my xp installation so i just backed out of it and decided to come here and see what the deal is. :)

---

### Post by Sayonara on 2007-07-14
Hi TourTex.

The problem seems to be something along the lines of Ubuntu not natively recognising the discs as belonging to a RAID array - I am having the same problem. You need to download the debootstrap and dmraid packages via synaptic package manager and do lots of tweaking to get it to work.

There are a couple of threads already that describe how to do this but I have stupidly not added them to my subscribed threads list! I was just looking for them when I saw your post.

So basically, it CAN be done, and the instructions are laying about somewhere in the installation forum...

[edit] Just to clarify... Linux has great support for proper RAID, but many new motherboards use "fake" hardware RAID, which is what causes these problems. So I hear.

---

### Post by TourTeX on 2007-07-14
Hello thank you for the update i didnt think anyone would answer if you find it could you post the links ? i'd greatly appreciate it.

---

### Post by Sayonara on 2007-07-28
It is here:
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

Good luck!

---

