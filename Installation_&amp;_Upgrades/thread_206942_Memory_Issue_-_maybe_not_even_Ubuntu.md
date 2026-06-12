---
title: "Memory Issue - maybe not even Ubuntu"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by jp-newtolinux on 2006-06-30
..Love Ubuntu..very few problems.  Spreading the word.

Anyway.

I bought some more memory for my PC with Ubuntu.
A Dell Precision 210, ECC SDRAM & SCSI adapter.

The Set up:
I needed more RAM in my PC.
No problem.  I had 4 slots with an existing 128.  I bought 3 more at 128 each...for 512 total.
After installing, Ubuntu sees 515.

Now... I have ECC SDRAM and I know this is occasionally a hassle.
My guess is that the newer chips have and extra 1meg of RAM (actually 129 per card) and that is used in the error correction (1 Old Card, 3 new cards with 1  extra each on the new ones = 515)

The BIOS is up to date.

The problem:

I have four slots and my motherboard/BIOS (not sure which one is the official bottleneck/gatekeeper) indicates a MAX of 512.
After 1 reboot and the system learning the new memory, the system locks.  I am guessing this should be expected because of some overflow issue.
Why do I think this?  I took out one card and all was well.

The question:

Can I somehow (through some configuration..whatever) tune the memory down to "max out" at 512?
This way I do not have to return one of my cards, which cost ~$40 each, (since it would be useless in a "discreet function" sense) and I would also have only 384meg (3*128) versus my desire to max out closer to 512.


TIA


jp

---

### Post by Dr. Nick on 2006-06-30
hmm not sure on the 129 mb bit.

I would be more likely to think that it has something to do with matching pairs or a defective/incompatible stick, I know that pairs used to matter, but not sure if it would have a affect if you just had 1 stick to begin with.

What I would do is put the origional stick in ths slot nearest the processor and put a new stick next to it. I would try various pairs of 2-3 pieces at a time and see if it works. My have a bad stick that freezess it. 

You could also plug them all in and use memtest from the ubuntu grub screen to test it out.

---

