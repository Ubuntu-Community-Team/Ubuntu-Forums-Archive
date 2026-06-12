---
title: "Stopping System V runlevel compatibility"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by kinsago on 2012-06-07
Hi all.
I've recently reinstalled Ubuntu 12.04 64bit on my PC as I am now dualbooting with XP because I want to play games that wine doesn't like.

Anyway I now can't boot Ubuntu because it hangs with the following message: "Stopping System V runlevel compatibility" 

I've tried update and upgrade from recovery menu using the root shell and I can't see any disk faults from the system information. I haven't used any proprietary drivers as I haven't logged in since I installed yesterday. Also, live cd/live usb works fine with no issues either...

I also can't login by switching to tty1 using ctrl-alt-f1(to manually startx as suggested) because when I type in username and password it flashes up a message (welcome message I think) and then returns me to login prompt. However, running startx from root shell does give me a screen but no real access to anything. FailsafeX fails.

I have run 12.04 on my system before, it is certainly capable and specs are below. The only difference from my normal installations is that this time I have my /home on a separate drive due to disk size limitations.

Any ideas and sorry if I've missed anything really obvious.

Regards

Kinsago

PS - Specs
Intel Core 2 Quad
4Gb RAM
220Gb free space on root partition (ext4)
about 300Gb free on /home drive
nvidia Geforce 8500 GT

---

### Post by kinsago on 2012-06-08
Ok, I'm going to mark this as solved. It's not really, but I have found a way round it by installing the 32bit version of Ubuntu instead of the 64bit version. no idea why this makes a difference as my system is 64bit but hey-ho.

Anyway, I'd still be interested in a solution if someone has one...

---

### Post by nuclearj on 2012-06-19
> **kinsago said:**
> Ok, I'm going to mark this as solved. It's not really, but I have found a way round it by installing the 32bit version of Ubuntu instead of the 64bit version. no idea why this makes a difference as my system is 64bit but hey-ho.

Anyway, I'd still be interested in a solution if someone has one...

It's not technically solved right?  Anyways, I am looking for a solution as well.

---

### Post by Subito Piano on 2012-07-25
NuclearJ -- any solutions?  I am about to wipe and reinstall (groan)

---

