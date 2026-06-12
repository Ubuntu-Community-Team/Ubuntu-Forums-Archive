---
title: "USB randomly failing and random automounts"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by oooooops on 2007-05-06
I've been using Ubuntu (well Kubuntu) since Dapper.  Dapper to Edgy was a clean instal.  For Edgy to Feisty I used the "recommended" upgrade path.  

Since installing Feisty I have had a couple of "random" issues that I'm not sure where to even start at.  

I preface tihs by saying I pass noapic irqpool to the kernel at boot time otherwise my NIC ceases working (e.g. if you remove one or the other it fails to work though it's still recognized).  This has been in effect since Dapper.

Currently in Feisty I have the following 2 random issues happening.

1)  In KDE, at random times I'll see an Automount window pop up, Then it mounts my DVD drive, the mount icon shows up on my dekstop.  Not just once, but over and over and over.  The icons just keep on stacking up.

2)  USB randomly stops working.  If I reboot I appear to have random odds of whether or not USB willl be recognized.  Sometimes it does, and sometimes it doesn't.  I don't see anything in /var/messages/logs one way or the other (dmesg) but perhaps I should be looking elsewhere.  When it works lsusb shows 3 entries, when it doens't lsusb shows absolutely nothing.  

Can anyone point me in the right direction on either of these/

---

### Post by derrekito on 2007-05-06
In all honesty, I would seriously recommend a clean install from a feisty disk.  Otherwise I'm going to be stuck asking stupid questions like: is it plugged in right?  

I recall I had an unbelievable amount of issues migrating from Dapper to Edgy.  I didn't even bother to chance with Edgy to Feisty.

---

### Post by oooooops on 2007-05-08
Yea it's plugged in right.  I have restarted with the older kernel 2.6.17-11 and now everything is magically fine.  So I suspect it's a kernel issue somewhere ...

---

