---
title: "Gutsy DVD integrity check sometimes fails"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by eye208 on 2007-10-22
I downloaded the Ubuntu 7.10 DVD ISO file. The MD5 checksum matched the one in the official MD5SUMS file, so I wrote the image to a DVD+R. The DVD checksum was correct too. Fine.

Then I booted from that DVD and ran the integrity check (yes, I'm paranoid). It told me there were errors in 1 file. I booted Feisty again (from HD) and re-checked the DVD. Still the same MD5 checksum. I checked the md5sum.txt file from the DVD. No errors. I booted the DVD and ran the integrity check again. At some point the splash screen disappeared and errors were thrown onto the console ("ata2: Buffer I/O error at xxxxxxx ..."). I pressed the computer's reset button, booted Feisty from HD and checked the DVD again. No errors. I ran the DVD integrity check a third time. No errors found! Fourth time: No errors found.

That happened yesterday. Today I gave it another try. I booted Feisty, checked the DVD twice. MD5 checksum correct. I booted the DVD. Errors in 1 file. I could not yet reproduce the Buffer I/O error though.

My system: Core 2 Duo, Intel P35 chipset, Nvidia 7900 GS, Samsung WriteMaster DVD drive (S-ATA, AHCI-configured), 2 GB RAM (XTC Platinum), Samsung HD (S-ATA). I checked the RAM with memtest, it's OK. The machine is rock-solid with Feisty. Every time I check the DVD in Feisty, it's OK. When I run Gutsy's own integrity check, it fails sometimes, but not always.

What's going on here?

---

