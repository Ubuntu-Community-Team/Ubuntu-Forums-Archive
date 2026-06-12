---
title: "Ubuntu Studio Gutsy - low latency kernel"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Blind Tiger on 2007-10-20
Howdy --
I just upgraded to Ubuntu Studio Gutsy from Fiesty.  Everything went well.  My concern though is that the kernel listed at Grub load time is the general one, not the low latency version.  If the 2.6.22 low latency kernel has been released, how do I go about upgrading to it?  Thanks.

---

### Post by MetalMusicAddict on 2007-10-20
> **Blind Tiger said:**
> Howdy --
I just upgraded to Ubuntu Studio Gutsy from Fiesty.  Everything went well.  My concern though is that the kernel listed at Grub load time is the general one, not the low latency version.  If the 2.6.22 low latency kernel has been released, how do I go about upgrading to it?  Thanks.

The -lowlatency kernel was obsoleted by -rt. **sudo apt-get install linux-rt**

---

### Post by Blind Tiger on 2007-10-20
Thanks MetalMusicAddict, I'll apt-get it done.

---

### Post by CheShA on 2007-11-07
Nice one, Metal Dude.  That one had me stumped for all of 10 minutes thanks to you.

---

