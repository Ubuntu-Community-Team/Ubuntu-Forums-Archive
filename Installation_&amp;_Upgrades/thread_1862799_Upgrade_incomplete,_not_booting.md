---
title: "Upgrade incomplete, not booting"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2011-10-17
I am rather disappointed about the Ubuntu upgrades -- there was not a single upgrade I did not have trouble with.

I tried to upgrade my Lenovo Thinkpad T-500 

This time, the upgrade process complained:
"Could not install /var/cache/apt/archives/samba_2%3a3.5.11~dfsfg-1ubuntu2_i386.deb" 
Then "could not install package samba"
Finally the upgrade process was ended without being successfully completed and I was informed that the system might be in an incomplete state.

Since this happened to me already several times in previous upgrades (on other computers too) it was relatively easy to fix the installed packages problem by using chroot to go into the broken system using this method: [http://wiki.ubuntuusers.de/chroot/Live-CD](http://wiki.ubuntuusers.de/chroot/Live-CD)

However the system still did not boot into the login screen. 

As it turned out, like after the last upgrade, disabling the 3D graphics chip and swithing to on-board graphics solved that.
(The system has a ATI Technologies Inc. Mobility Radeon HD 3650)

But now I am left with a Thinkpad without the ability to use the 3D graphics (which I need). 

This chip is not new at all and it is quite common too ... why does Ubuntu still not manage to deal with it? This is rather frustrating. :(

---

