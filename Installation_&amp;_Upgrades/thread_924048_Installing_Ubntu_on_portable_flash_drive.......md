---
title: "Installing Ubntu on portable flash drive......"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by jakewc2 on 2008-09-19
Hi, I want to set get a large flash to install Ubuntu on, which I;m hoping to get next week. I already have a 4gig one, and want to practice, I was wondering if somebody could point me in the right direction to Install it. 

I was wondering, can it be used on a computer different to the one that I installed it from. If it can, how?

Thank you for your help.

John.

---

### Post by Herman on 2008-09-19
> Hi, I want to set get a large flash to install Ubuntu on, which I;m hoping to get next week.  Make sure you buy a good quality one. Read the manufacturer's specs and advertised performance charactristics. Look for one with good wear levelling and good read and write speeds. Also, look for one with good wear properties, for example, with over 100 000 rewrite cycles. Preferably, look for one with a ten year warranty or a lifetime warranty.
Sometimes, good quality flash memory can be purchased cheaper than poor quality. Ignore USB flash memory that costs extra because it has special software for use with Windows. You should be able to buy one with good quality material but without the software for around the same price as poor quality flash memory with fancy software.
> I already have a 4gig one, and want to practice, I was wondering if somebody could point me in the right direction to Install it. 
Just install it.
I use and recommend the reiserfs file system instead of ext3 for USb flash memory installations. Reiserfs is much faster to write to some flash memory controllers, and at least the same speed as ext3 for others.
Make sure you click 'Advanced' when you get to step 7 of the installation and select the USb drive's MBR for the place to install the boot loader to, not you computer's internal hard drive.
> I was wondering, can it be used on a computer different to the one that I installed it from. If it can, how?Yes, it can, just plug it into a different computer and boot it.
It might take a little bit longer to boot in a strange computer, but Ubuntu Hardy Heron can configure itself automatically for most computers now. Older versions of Ubuntu couldn't do that.

---

