---
title: "Generate install iso from my current running system??"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by gorlash on 2008-02-07
I have installed Ubuntu 7.10 server on a system, installed a couple-dozen additional packages that I want to use, and did some other customization.  I now have a machine working *exactly* as I want all our machines to run.  

Is there some way to generate an iso from this existing system, so I don't have to answer all the questions, and download all the modules again??

I looked at InstallCDCustomization documentation page, but that doesn't seem like really what I want, besides being enormously complex.  I would really like to generate a target system directly from this one...  Is that possible??

---

### Post by pytheas22 on 2008-02-07
I don't know how to make an ISO, but you could make an image of your existing install and simply ghost it directly to the hard disks of your other machines.  Take a look at [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) .

---

### Post by gorlash on 2008-02-07
Okay, I'll try that out - that's actually what I really wanted... (to *duplicate* the disk, not to create an ISO...).  However, PartImage seems to duplicate individual partitions, while I'd prefer to actually dup the entire disk!!

I tried using dd awhile back for this purpose, but it doesn't seem to be a very clean process; I always have to do an fsck on the target when it is first booted, and occasionally the target was corrupted, which isn't very reassuring...

---

