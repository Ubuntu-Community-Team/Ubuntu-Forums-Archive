---
title: "Kernel upgrade 2.6.23.1"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by steveneddy on 2007-10-21
I have noticed on kernel.org and the bluez.org that there is a new kernel available and a patch available for the Bluetooth stack.

Any idea when we may see this kernel upgrade and if the patch will be implemented?

Or do you think that it would be easier to compile my own kernel and then apply the patch?

Any help welcomed.

:popcorn:

---

### Post by 5-HT on 2007-10-21
Would be easier to patch your own custom one methinks.
While the kernel itself for any particular will not get upgraded, backported patches can find themselves showing up in some updates--though being few and far in-between.

I wouldn't hold my breath for the Bluetooth stack tough considering that mac80211 never got backported but you never know...
cheers,

---

### Post by DizzyTech on 2007-10-21
I wish they would update to 2.6.23, it would fix the regressions on my (soon-to-be-deprecated) laptop.

---

### Post by steveneddy on 2007-10-21
I tried to compile my own kernel tonight. It was an experience that I will try on another machine in the future, one that I don't have to use for work. 

I almost hosed my system. There were no nvidia drivers in there, so the monitor on my laptop was screwy. The bluetooth would not hook up. Wireless was non-existent.

Next time I will pay closer attention and try it on a machine that i can play with more.

I booted into the stock kernel, reset the nVidia driver in Restricted Driver Manager and deleted any instance on the custom kernel that I made and took it out of the grub menu.

But I did learn a very important lesson. You have to go through every option to look at all of your hardware to get everything to work correctly.

As far as the bluetooth is concerned, I found out the problem and corrected the config file and it hooks up at boot time just like I wanted it to.

:popcorn:

---

