---
title: "Acer Aspire One users! Bootup/hibernation issue."
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ikt on 2010-03-06
I have the AAO ZG5, Just enquiring if anyone else has this issue:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/531650](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/531650)

I also have an issue with hibernation, where it will hibernate but logging back results in the 'log back in' window just freezing on 'checking...'

These both were working fine as of Alpha 2 but since the updates to  alpha 3 they aren't working, these are pretty significant regressions for me, so I'm just wonder if anyone else is having these issues?

---

### Post by DavidOC on 2010-03-06
> **ikt said:**
> 

I also have an issue with hibernation, where it will hibernate but logging back results in the 'log back in' window just freezing on 'checking...'


I'm using Alpha 3 on an AOA150 and I can confirm this.  I've checked top when this bug occurs and it turns out that the program gnome-keyring-d uses all of the cpu when trying to log in.

---

### Post by ikt on 2010-03-07
> **DavidOC said:**
> I'm using Alpha 3 on an AOA150 and I can confirm this.  I've checked top when this bug occurs and it turns out that the program gnome-keyring-d uses all of the cpu when trying to log in.

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/524860](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/524860)

This would be the bug report for that issue.

I hope it's fixed in time for lucid :/

---

### Post by ikt on 2010-03-08
> **ikt said:**
> I hope it's fixed in time for lucid :/

It is ! Yay!

The only other bug I have is:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/531650](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/531650)

Anyone else able to reproduce?

---

