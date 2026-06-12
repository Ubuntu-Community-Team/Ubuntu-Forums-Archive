---
title: "The ext3 file system creation in partition #7 of SCSI3 (0,0,0) (sda) failed."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Pf123 on 2007-10-18
Ok, so I downloaded Ubuntu 7.10 today, and have been running off the LiveCD, but when I click the install icon on the desktop, I follow everything, i make a swap partition, and I make a partition for ubuntu, swap is 260mb, partition for ubuntu is roughly 97gb.

Then I hit next, I put in my name and password, next again, i review to make sure everything is good, and hit install.  After a few seconds, I get this:

> The ext3 file system creation in partition #7 of SCSI3 (0,0,0) (sda) failed.

I've installed earlier versions of ubuntu on other machines, never seen this, and I'm not all that good at linux either.  Anyways, I have the 64 bit version of Ubuntu.

Computer specs:
3.2ghz 640 P4
1gb DDR2 ram
250gb harddrive partitioned in 3 (xp, vista, soon ubuntu)

Let me know if you know how to solve this, or need any more information.

---

### Post by alphacrux on 2008-02-24
yeah i had the same problem, it would always stop at #7 no matter which order I tried to partition. I heard from someone that the partitioner tries to mount the drives right after they are created which is what is causing the problems. I also noticed that the partitions were showing space being used inside them even right after I created them. I dont know what the deal is but i just used the gparted application in the live cd to create my partitions first. Then i ran the install program and used the partitions i created mounting them to what i had planned them out to be (/, /usr, /var, etc...). I hope this helped :)

---

### Post by alphacrux on 2008-02-24
Actually i found out there should be parts of the partitions used for the ext3 journaling so that isn't part of the problem. Also the live cd partition editor is in System -> Administration -> if you're wondering.

---

