---
title: "Problem finding disk AND possible display issue with 7.10"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by Thanatus on 2008-02-22
I tried a live install of 7.10, no cigar.

Yes, I checked the CD

Yes, I tried alternate CD.

I got the black screen that a lot of people seem to be getting.

Yes, I have an 8800GTS... oh bother.

However I seem to have another problem as well, one that people trying to install on external drives usually have:

```
ata1: (irq_stat 0x00000040, connection status changed)
ata1: soft resetting port
ata1: SATA link down (SStatus 0 SControl 300)
ata1: EH complete

exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0x2 frozen
```

This is probably because my drive is not on the very first port (it's a BYI and I had to make adjustments in a cramped space).

I've added the boot paramaters like noacpi, nosplash, etc.

I might get started going somewhere if someone could tell me what parameter to add to make the loader auto scan for a HD (I only have one).

Then, of course, I will need to know what to do about the 8800GTS situation, if anything CAN be done...


Regards, and thank you in advance

P.S. I'm using the 64-bit

---

