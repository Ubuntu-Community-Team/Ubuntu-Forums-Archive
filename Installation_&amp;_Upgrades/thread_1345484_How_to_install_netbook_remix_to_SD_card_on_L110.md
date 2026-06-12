---
title: "How to install netbook remix to SD card on L110?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by udippel on 2009-12-04
I am very happy with my L110 (the Linpus-version,with 8GB of flash and an SD-expansion).
Now I tried to install it to run '/' from the SD-card (ought to be faster).
I noticed, the BIOS can't see it, so I put /boot/ on sda; the built-in drive and everything else on the SD (that is '/').
And still it won't boot. It starts okay, but fails to find the UUID of the root partition. 
So I assume, that the init kernel can't recognize the SD drive. Is this correct? And if it is, how to make it work; how can I tell the /boot partition to load (what?) as driver for the SD card?

Thanks a bunch in advance,

Uwe

---

