---
title: "Upgrade Anxiety"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by wbjoly on 2011-01-03
Ok so I have been hesitant about upgrading to a new version.  I am still running 8.something.  My computer has become VERY slow.  I am wondering if it could be because I am running an old version. 

So I went to upgrade via 'Update Manager' to 9.04 but upon install a message popped up that there is no driver support for my video 'AMD 'fglrx' graphics driver'

What should I do?  would there possibly still be the same issue with 10.10?

---

### Post by mastablasta on 2011-01-03
> **wbjoly said:**
> Ok so I have been hesitant about upgrading to a new version. I am still running 8.something. My computer has become VERY slow. I am wondering if it could be because I am running an old version. 

 
No that's probably not the reason why computer is slow.
 
 
> 
So I went to upgrade via 'Update Manager' to 9.04 but upon install a message popped up that there is no driver support for my video 'AMD 'fglrx' graphics driver'
 
What should I do? would there possibly still be the same issue with 10.10?
 
AMD (before ATI) probably dropped their support for your graphics card. which means you will use opensoruce drivers from version 9.04 onwards. it's not really an issue if opensoruce drivers work well with your card. they do with mine, but some people reported slowdown or bad graphcis or no 3D acceleration...
 
 
it might be a good idea to try a clean install of the system to get rid of the old stuff completelly.

---

### Post by houseworkshy on 2011-01-03
I don't know, however, if you can spare a blank cd you could try burning a copy of 10.10.  Then try it in the live cd mode ( try ubuntu without changeing your system or words to that effect ).  If that runs ok try using the update manager, even though in live cd mode you can only install to ram, which would be pointless as drivers require reboots, it would at least do a bit of auto detecting and list any appropriate drivers found.
Personally I'd recomend 10.04.whatever it is now instead.  Use a freshly downloaded iso as the .somethings fix a lot of bugs and save a lot of megs and time during post install updates.
As a general rule it is better to backup and do clean installs than distribution upgrades online.  It is also better to use write once only cd's rather than re-writeables.  To save future hassles you could also put "home" in it's own partition, there are plenty of guides floating around the forums on that.

---

### Post by wbjoly on 2011-01-03
I would love to do a clean install but I have no clue how. :confused: My friend that was going to help me has been putting me off for three months now and its getting to the point that I can barely get anything done because my comp is so slow.  Actually its only Firefox that is slow and its always messing up.

Ideally what I want to do is not only do a fresh install but create a dual boot system so that I can start using QuickBooks.

---

### Post by mastablasta on 2011-02-15
you just back up data, boot form CD and format the disk, create two partition (for example one is NTFS for win), then first install windows and then Ubuntu to the free empty disk space.

---

