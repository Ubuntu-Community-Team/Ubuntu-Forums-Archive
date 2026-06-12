---
title: "CPU switch PIII to Celeron"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by prkfriryce on 2007-02-23
I'm not so sure edgy is hot swappable with CPUs... 

i'm going to be switching a 1.0GHz PII with a 1.5GHZ Celeron CPU and wondering what, if any, are the prereqs I should be taking? 

I did a few searches, but they were probably too generic, what will be the repercussions if I go ahead with my current 6.10 running on the PIII to the Celeron??

---

### Post by tgalati4 on 2007-02-23
What ever you do, don't let the smoke out.


Shouldn't be a problem.  Note the following:

dmesg | grep MIPS

Before and after.  I am guessing you will go from 1,000 BogoMIPs to 1,500 BogoMIPs.

Call me a liar.


Oh, two other things.  Don't cut your fingers with the spinning fan.  Hold the new CPU in one hand, remove the other CPU with the other hand and do it quickly before Edgy finds out.


Don't forget the thermal grease.  It's there for a reason.  Not too much, just a thin coat.

---

### Post by maxamillion on 2007-02-23
Unless its a "new gen" celeron, you will be wasting your time because last time I checked the 1ghz PentiumIII Coppermine cpre (which I assume is what you have) was able to keep up with a 1.4GHz P4 willamette core and dominate celeron coppermine-128s up to roughly 1.8ghz (and i assume since you are swapping them in the same motherboard that the celeron is the socket370 and thus makes it a crippled coppermine)

... just a thought.

---

### Post by prkfriryce on 2007-02-23
> **tgalati4 said:**
> What ever you do, don't let the smoke out.


Shouldn't be a problem.  Note the following:

dmesg | grep MIPS

Before and after.  I am guessing you will go from 1,000 BogoMIPs to 1,500 BogoMIPs.

Call me a liar.


Oh, two other things.  Don't cut your fingers with the spinning fan.  Hold the new CPU in one hand, remove the other CPU with the other hand and do it quickly before Edgy finds out.


Don't forget the thermal grease.  It's there for a reason.  Not too much, just a thin coat.
thanks, I'll make sure to tell Edgy to go play hide-an-go-seek while I swap em'  :) 

> **maxamillion said:**
> Unless its a "new gen" celeron, you will be wasting your time because last time I checked the 1ghz PentiumIII Coppermine cpre (which I assume is what you have) was able to keep up with a 1.4GHz P4 willamette core and dominate celeron coppermine-128s up to roughly 1.8ghz (and i assume since you are swapping them in the same motherboard that the celeron is the socket370 and thus makes it a crippled coppermine)

... just a thought.

I didn't really think about the performace specs on the two CPUs before hand. I had the extra hardware so I figured, might as well try it before doing a full MB/CPU/memory upgrade. 

I'll give it a shot this weekend and hope for the best!

---

### Post by Kateikyoushi on 2007-02-23
Please let us know about the outcome, I also have a machine with 1.2 Celeron and want to upgrade it, the machine is an LCDpc so full upgrade is not possible I wonder a PIII 1.4 would be faster then I would grab one somewhere.

---

### Post by tgalati4 on 2007-02-23
Max may be correct.  I have a 500 MHz PIII Dell Optiplex that gives 1,000 BogoMIPS and 1 GHz Celeron that also gives 1,000 BogoMIPs.  The PIII coppermine is an upgrade from an old PII, Slot I card, so I can't swap them to compare in the same motherboard.  The Celeron is a cheaper, lower power, consumer-grade processor so it's possible that the performance will be the same.  Call myself a liar.

---

### Post by esaym on 2007-02-23
> **tgalati4 said:**
> 

Oh, two other things.  Don't cut your fingers with the spinning fan.  Hold the new CPU in one hand, remove the other CPU with the other hand and do it quickly before Edgy finds out.




Are you really serious that a cpu can be changed while it is running :confused: :shock:

---

### Post by Kateikyoushi on 2007-02-23
I am sure he refers to Cpu hot swapping. ;)

---

### Post by tgalati4 on 2007-02-23
If you see smoke, then you weren't fast enough.

---

### Post by prkfriryce on 2007-02-23
> **tgalati4 said:**
> Max may be correct.  I have a 500 MHz PIII Dell Optiplex that gives 1,000 BogoMIPS and 1 GHz Celeron that also gives 1,000 BogoMIPs.  The PIII coppermine is an upgrade from an old PII, Slot I card, so I can't swap them to compare in the same motherboard.  The Celeron is a cheaper, lower power, consumer-grade processor so it's possible that the performance will be the same.  Call myself a liar.

I'll let you know the BogoMIPs when I try

> **tgalati4 said:**
> If you see smoke, then you weren't fast enough.

the real trick is to try it blind folded  :-\"

---

### Post by tgalati4 on 2007-02-23
Just feel for the clipped corner of the processor.  Intel products have always been ADA compliant.

---

