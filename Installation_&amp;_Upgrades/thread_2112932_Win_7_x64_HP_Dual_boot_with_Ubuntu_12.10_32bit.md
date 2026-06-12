---
title: "Win 7 x64 HP Dual boot with Ubuntu 12.10 32bit"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by mercurial88 on 2013-02-06
Hey guys, i am planning to install ubuntu on my Acer Laptop i have 320 GB space and 3GB of Ram, so i wanted to know how much space should be allocated ?

Was thinking

50GB - Win
100MB - Sys Res

25GB - /Root Part
2GB - /Swap

P.S. i dont keep my system on Hibernate.

shared - approx 200-225GB

Is this good enough ?

Thanks for your time and replies. :)

---

### Post by Mark Phelps on 2013-02-06
Space aside, be sure that BEFORE you go to install Ubuntu, you do the following:
1) Use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need this later to restore Win7 boot if that gets damaged during the dual-boot setup.
2) Use the Win7 Disk Managment utility to shrink the Win7 OS partition to leave room for Ubuntu.  Do NOT create another partition at this time.
3) Reboot into Win7 a couple of times to allow it to make filesystem adjustments from the shrinkage.

---

### Post by oldfred on 2013-02-06
+1 on Mark Phelps's suggestions.

Why 32bit. You should just install the 64 bit. I only have 1.5GB RAM and run the 64bit version although that is not normally suggested for that little RAM. And I run fallback so I am not running Unity which seems to need more RAM. 
But any system with 3GB or more should use 64bit version.

Your partition plan seems fine. What partitions do you have now, as you will need one primary to make into an extended for the logical partitions you need to make.

---

### Post by mercurial88 on 2013-02-06
Just thought there were some issue's with the x64,henceforth will go for the x64..i am gonna shrink my C:\ 150 Gigs to 130 so it will be as follows

100mb system Res
C:/ 130 Gigs
D:/ 150 Gigs

/swap 2Gigs
/Ext 4 18 Gigs

No System recovery part, as i have already deleted the partition. so overall 4 Primary partions

Also a quick question i am also planning to install Ubuntu x86 on a older Desktop lying around, it's a Intel P4 with 1 gigs if RAM, what would you suggest 12.10 or 12.04? i feel 12.10 might be a lil heavy on that config

---

### Post by oldfred on 2013-02-07
It is not 12.04 or 12.10. It is if it is new enough to have the PAE extensions. Pentimum M and all chips before that do not have PAE and now full Ubuntu only works on "newer" chips with PAE. 
       [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

    

And it is video that is the bigger issue with full Ubuntu. I have 1.5GB RAM with Intel video but a dual core and it runs full Ubuntu 12.04 with fallback (not Unity) better than it ran 10.10.

You may want to consider Xubuntu or Lubuntu as they require less resouces and less video horsepower.

---

