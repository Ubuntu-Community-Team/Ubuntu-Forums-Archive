---
title: "YAPQ - Yet Another Partion Question"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by phpShawn on 2007-12-20
Hello!  I am yet another Windows XP person planning to "upgrade" to Ubuntu instead of going Vista.  However, before I take that jump I'm going to dual boot for a while to test it out.  

During the install of 7.10 I get to the partition step and am presented with this slider:

[IMG]http://www.eventslink.net/temp/partition1.png[/IMG]

On my laptop I have only 18.3G of free space and the slider's minimum partition size is 18.9G.  The instructions make me think that the partitioner is setting up the Windows partition and then will setup the two Linux partitions later.  Am I correct?

I also went to GParted and setup the below partitions.  If this is correct, should I just go ahead and do this off the LiveCD and then go back and run the installer?

[IMG]http://www.eventslink.net/temp/partition2.png[/IMG]

Thank you all for this excellent forum!

Regards,
Shawn

---

### Post by logos34 on 2007-12-20
> **phpShawn said:**
> On my laptop I have only 18.3G of free space and the slider's minimum partition size is 18.9G.  The instructions make me think that the partitioner is setting up the Windows partition and then will setup the two Linux partitions later.  Am I correct?

I also went to GParted and setup the below partitions.  If this is correct, should I just go ahead and do this off the LiveCD and then go back and run the installer?

Basically it's just indicating 18.9 is the smallest it can shrink sda2. You chose 29 gb instead, that's fine.

What you have looks ok (although more swap than you probably will ever use).

So it looks like you have a recovery partition in sda1, XP in sda2, and what you will end up with is root in sda3, and /swap in sda4 (or sda5 if it makes sda4 an extended partition and puts swap inside, as it usually likes to do).

---

### Post by phpShawn on 2007-12-21
Thanks!  I just went through the installer and the new partition slider definitely was referring to the Windows partition.

Thanks again!
Shawn

---

