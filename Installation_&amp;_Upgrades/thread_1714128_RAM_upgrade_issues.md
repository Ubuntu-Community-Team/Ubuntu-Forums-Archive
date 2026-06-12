---
title: "RAM upgrade issues"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by indiana_crook on 2011-03-24
Hello all!  This is more of a hardware issue than a Ubuntu issue, but I'm hoping to employ the great wisdom of the Open Source community.  I have an ACER Aspire M5100.  It has 2GB of DDR2 RAM.  I want to install 4GB. The computer will not boot if I put in more than 2GB.  Any ideas?  ACER support says they have to be 1GB sticks in each slot, but it will work fine with one 2GB stick.  Anything more than 2GB sends my computer into useless mode...

---

### Post by Hedgehog1 on 2011-03-25
indiana_crook,

According to the tech specs from acer, that unit will support 4 gigs of RAM:

[AspireM5100 Specifications]("http://support.acer.com/acerpanam/desktop/0000/Acer/AspireM5100/AspireM5100sp2.shtml")

Oddly, those same specs say:

> Up to 4 GB DDR2 533/667/800 MHz SDRAM 
(dual-channel support on **four **DIMMs)

This seems to indicate the model the are referring too will only accept 1 gig DIMMs.

How many memory slots does your unit have?  If it is 4 slots, you will need to use four 1 gig DIMMs.

***The Hedge***

:KS

**p.s. It looks like they memory folks only sell 1 gig DIMMs for this unit: [M5100-Memory]("http://www.edgetechcorp.com/ram/Acer/Aspire/M5100-Memory")**

---

### Post by ~Plue on 2011-03-25
> **Hedgehog1 said:**
> 
This seems to indicate the model the are referring too will only accept 1 gig DIMMs.
> 
                             Up to 4 GB DDR2 533/667/800 MHz SDRAM 
(dual-channel support on **four **DIMMs)                      
How many memory slots does your unit have?  If it is 4 slots, you will need to use four 1 gig DIMMs.
iiuc, thats not entirely true;
it means 4 slots (two pairs) which supports dual-chanel (when the same spec pairs of sticks used in the same color slots)
but the maximum that the board can support is 4gb, regardless of the size of each stick

---

### Post by Hedgehog1 on 2011-03-25
> **~Plue said:**
> iiuc, thats not entirely true;
it means 4 slots (two pairs) which supports dual-chanel (when the same spec pairs of sticks used in the same color slots)
but the maximum that the board can support is 4gb, regardless of the size of each stick

Yup - you are correct.  They folks who sell the memory do indeed offer 2gig DIMMs for this system. (I read 1x2GB as 2x1GB).

So this means that 2 2gb DIMMS in slots 1 & 3 OR in slots 2 & 4 would be OK then, right?


***The 'out-of-memory-error' Hedge***

:KS

---

