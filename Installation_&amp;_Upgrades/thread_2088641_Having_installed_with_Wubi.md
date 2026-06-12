---
title: "Having installed with Wubi"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Dsoslglece on 2012-11-27
Hi,
I've installed Ubuntu on an old PC to replace XP on it (at the moment both are on it).
And, to do so, I used the Wubi installer.

everything seems OK, except the OS being rather slow to react.
Using often Ubuntu on my iMac (parallels desktop), I know that it is normally just as efficient and swift as Mountain Lion, and so (even if this could be caused by the rather restraint RAM of this machine), I investigated a bit and it appears that (from Ubuntu desktop) it is Ubuntu 64 bits.

I'm rather surprised by this, since I thought the machine was a 32 bits. 
In another hand, I couldn't find any indication of this from the XP side, but I must admit that not being such a fan of windows, I'm not really much accointed with the meanders of its guts, so I may have missed it.

Also, is it possible that the Wubi in downloading the system would have made a mistake?

And also, is it possible for Ubuntu 64 bits to work (even if a bit slowly) being installed on a 32 bits machine...
This could also explain the fact that in doing the updates yesterday, it reported a fault and lot of them (on a total of 200MB) was uncompleted.

Thanks in advance for any advice

---

### Post by howefield on 2012-11-27
> **Dsoslglece said:**
> And also, is it possible for Ubuntu 64 bits to work (even if a bit slowly) being installed on a 32 bits machine...

If the machine is 64 bit capable then yes, it would work even though you are running a 32 bit XP install.

Wubi installs can be a bit slower as you are running two file systems, one on top of the other, wubi is good for evaluation but not really for long term use.

Have you checked for proprietary drivers which may help the response of the OS. Or more likely, you may be better off with a lighter version. Whcih version of Ubuntu have you installed ?

---

### Post by Dsoslglece on 2012-11-27
Thanks Howefield for the quick answer…

The thing is that the system installed seems to be 64 bits, but I thought that the machine itself was 32.
So, I could conceive that a 32 bits system would maybe work on a 64 bits busses, but not really the opposite!

Are you certain that having the two systems installed (but not working in parallel) is harder on the computer? since when a system is installed but off, it is just like any other folder, and only few GB…

This tincan has a disk of 250 GB, and so, is quite far from being full

I will try to find anyway, following your advice, some data from XP concerning the size of the busses.

---

### Post by howefield on 2012-11-27
> **Dsoslglece said:**
> Are you certain that having the two systems installed (but not working in parallel) is harder on the computer? since when a system is installed but off, it is just like any other folder, and only few GB…

Have a browse here, a few benchmark scores which although going back to late 2010 are still likely to apply.

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1)

---

### Post by Dsoslglece on 2012-11-27
Yeah, I see now!
So, it seems that when installed with Wuby, it is in fact like having a virtual Ubuntu inside XP…

so, I will make a clean install from an install DVD…

Thanks for the data.

---

