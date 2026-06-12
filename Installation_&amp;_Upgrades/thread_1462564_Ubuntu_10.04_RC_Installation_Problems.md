---
title: "Ubuntu 10.04 RC Installation Problems"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by johnproyal on 2010-04-25
This is my first time installing anything Linux. Everything seems to have gone right. I burned a Live CD, which loads, but the problem is once I choose ANY option, it changes into a black and white screen (feel like an idiot for calling it that. I'm new. I apologize.) and at the bottom, it says something like

```
0693453 kernal.thread.helper 0x7 0x9
```

and doesn't load anything else.

If there's any more information needed, tell me what to include. I really want to try Ubuntu.

My computer is a Toshiba Satellite L505D-S5983.

---

### Post by suryaccnamcse on 2010-04-25
make sure that your hard disk has at least 5GB of free space, ubuntu requires that for creating a virtual partition in which it will install grub.

---

### Post by johnproyal on 2010-04-25
Before starting, I made sure I had room to install. I have a partition for Windows 7 (200 gig), a media partition (100 gig) which I was going to use to share media between Ubuntu and Windows (following [this guide from Lifehacker]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")) and then unallocated space (30 gigs) I was going to use for this OS.

My computer is a Toshiba Satellite L505D-S5983.

---

### Post by suryaccnamcse on 2010-04-26
When installing Ubuntu on a system with a windows partition

1. Scan the disk for errors.can be done via the   setup utility or by clicking the right clicking windows partition selecting properties and clicking tools tab.

2. Defragment the hard disk.

3. Ensure that Windows is shut down correctly.

Then try installing Ubuntu from the cd or usb.

---

### Post by colinwhipple on 2010-04-26
> **johnproyal said:**
> Before starting, I made sure I had room to install. I have a partition for Windows 7 (200 gig), a media partition (100 gig) which I was going to use to share media between Ubuntu and Windows (following [this guide from Lifehacker]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")) and then unallocated space (30 gigs) I was going to use for this OS.

My computer is a Toshiba Satellite L505D-S5983.

Do a search of the forums on "L505D".  Lots of people are having problems with Toshiba L505D series laptops.

The simplest solution is to use a boot option of "acpi=off".  But that disables power management.  It gets you running with Ubuntu, but is not a long-term solution.

Colin

---

