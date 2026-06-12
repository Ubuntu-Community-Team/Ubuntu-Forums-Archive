---
title: "I give up! AMD64 iso always fails media check"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by Carl H on 2006-09-01
I've downloaded the iso for the AMD64 version five times, and burned each one several times at different speeds, different brands of media, and on different drives, and every time the resulting disc fails the media check. 

I requested a CD via Ship-It, which came earlier in the week. Guess what... it fails the media check!!!!!!

The offending file is always the same - ./casper/filesystem.squashfs

The media checker flies through the disc, then pauses for ages on this file before eventually saying "mismatch". 

Any ideas? There doesn't seem to be much point in downloading it again, as presumably I'd just get the same ISO that was used to make the Ship-It disc. I've already got a 32 bit installation, I really wanted a 64-bit one on my newly built 64-bit PC. :sad: :sad: :sad:

---

### Post by Carl H on 2006-10-02
Turned out that I had some duff memory, which must have been causing the media checker to give false results. 

I've changed the memory, and the media checker passes the discs. I now have a fully working fresh installation of 64-bit Ubuntu. 

Should this be recorded anywhere? Just in case it happens to someone else?

---

### Post by graven on 2006-11-11
Hey Carl H, Many thanks, I seem to have the same problem - so thanks for leaving the record. I have the same issue - will do the memtest and hope for the best. I was quite perplexed as I have already installed from this cd onto this PC. Nice one.

---

