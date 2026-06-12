---
title: "Fresh installs and driver issues"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by dduehning on 2010-10-10
Have been 'playing' with ubuntu versions since 7.04, and with each version, right off the bat, I've noticed that they lack drivers to enable wireless in the laptops I've used.  I have to physically connect via the ethernet adapter, then check for drivers that may be applicable to my system.  

Question is, after all these versions, why aren't the drivers included with the os?  I've used the same 2 laptops for the last 3 years, but yet this continues to be the first step after install that must be completed in order to enable the wireless.  I'm not a newb to the computing world, but I am to Linux.  This is somewhat discouraging to me and is what has continuously prevented me from making the switch permanently.

---

### Post by presence1960 on 2010-10-10
> **dduehning said:**
> Have been 'playing' with ubuntu versions since 7.04, and with each version, right off the bat, I've noticed that they lack drivers to enable wireless in the laptops I've used.  I have to physically connect via the ethernet adapter, then check for drivers that may be applicable to my system.  

Question is, after all these versions, why aren't the drivers included with the os?  I've used the same 2 laptops for the last 3 years, but yet this continues to be the first step after install that must be completed in order to enable the wireless.  I'm not a newb to the computing world, but I am to Linux.  This is somewhat discouraging to me and is what has continuously prevented me from making the switch permanently.

I understand your frustration. But after enabling the drivers with a hard wired connection why is that keeping you from making the switch permanently? That makes little sense to me.

---

### Post by dduehning on 2010-10-11
My reasoning, while it may seem silly to you...is that as I'm extremely new to Linux in general, I tend to muck it up pretty easily, and I'd rather not have to continue to do a hard wire to update the drivers, etc.  when it's so bad to warrant a complete reload.  After all, the best way to learn something is to just jump in and do it...imo

That being said, I still don't understand why ubuntu doesn't just include these drivers... the iso is already too big to fit on a cd, so since you have to use a dvd or flash drive, why not include the drivers so people don't have to update to get the proper drivers.  If Linux wants to be in any position to take over the os market, this is something that should not be overlooked.

If nothing else, a link to download would be a good start.

---

### Post by efflandt on 2010-10-11
The reason they are not included by default is that Ubuntu initially only installs things that are open source and certain drivers and codecs are not open source.  Many of them are on the CD, which you can install by adding the install CD to Synaptic repositories by checking a box in Synaptic, which is useful if you have no internet connection at all.  They are just not installed by default.

If you have a temporary network connection, it is even easier, usually by just going to System > Adminstration > Hardware Drivers (if Hardware Drivers does not prompt you automatically) to activate (install) special drivers you might need.

---

