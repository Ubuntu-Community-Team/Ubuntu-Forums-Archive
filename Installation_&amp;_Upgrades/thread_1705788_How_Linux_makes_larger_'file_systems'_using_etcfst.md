---
title: "How Linux makes larger 'file systems' using /etc/fstab"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by Hedgehog1 on 2011-03-12
[SIZE="2"]From the desk of ***The Hedge***[/SIZE]


I have noticed the (understandable) tendency of new Linux users to think about disk drives in the 'Windows way'; their first thought is to exchange a new drive for an existing one, rather than combine both drives for a larger 'file system'. 

There are times when replacing one drive with another is indeed the correct action (aging drive, failing drive, slow drive, etc).  But in other cases it may be preferable to use the inherent strength of the **fstab** (**f**ile **s**ystem **tab**le) file to combine physical drives to become a larger 'file system'.

Lets first look at a user with an 8 gig netbook who is running out of space.  Rather than replace the 8 gig flash drive with a 32 gig device, the old and new devices can be combined to yield a 40 gig 'file system':

[IMG]http://img863.imageshack.us/img863/6315/netbooksd.png[/IMG]

This same principle can be applied to a user with a computer using an 80 gig hard drive, and who 'adds' a new 320 gig drive instead of replacing the 80 gig drive with the 320 gig drive:

[IMG]http://img840.imageshack.us/img840/4129/laptophd.png[/IMG]

This same principle can also be applied to building a massive 'file system' without the requirement of using RAID:

[IMG]http://img853.imageshack.us/img853/6228/serverhd.png[/IMG]

The above 12 terabyte system can be built using a basic motherboard with four open SATA ports and four 3tb hard drives.  No server based equipment is needed; no raid hardware or software is required.  This is just something that Linux does (and does very well).

I hope these examples give you feel for the power of Linux 'file system' design.  Next time someone asks 'what is the big deal about the **fstab** file, anyway?', you can grin knowingly and say: "***I will tell you when you are older.***"


[SIZE="2"]***The Hedge***[/SIZE]

:KS

---

### Post by mörgæs on 2011-03-13
Thanks. It sounds interesting, but how do I do this? 

A step-by-step list of commands would be good to have.

---

### Post by Hedgehog1 on 2011-03-13
> **mörgæs said:**
> A step-by-step list of commands would be good to have.

mörgæs,

***Oh, like making the pretty pictures wasn't hard enough? ***:D

Are you thinking a step-by-step of all three?  Oddly enough, the 12tb one is the easiest (no moving of '/home' on that one).  The netbook example is from a real post a few days ago, where I found I wished I had a picture to help explain (although the poster got it working without a pretty picture).

I had been thinking of showing how individual hard drives can instead be separate banks of RAID arrays ('/payroll' array, '/payables' array, '/receivables' array, '/inventory' array) that can be mounted and unmounted for servicing without shutting down the main Linux box.  But I think that is more than the 'typical user' needs to know.  ***But it is cool.***

OK, I will add the step-by-step lists after the introduction area.  Thanks for the feedback.

***The Hedge***

:KS

---

