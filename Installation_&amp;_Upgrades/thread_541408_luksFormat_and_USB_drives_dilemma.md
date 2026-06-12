---
title: "luksFormat and USB drives dilemma"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by Cryptog on 2007-09-02
I've made several attempts to use cryptsetup to create a bootable USB drive with an encrypted root partition. In very few cases, it worked, but in most, the installation fails partway through with an I/O error on the target device. 

I've tried this on several USB drives, and only one works. When I run badblocks -w on the raw paritition of the drives that didn't work, it finds errors. Even on a USB drive that is brand new. So that's the problem...

But, if I was creating a normal partition, I could run bad blocks, etc, but if I use cryptosetup luksFormat, there is no way to recognize bad blocks on the drive. You have to have a perfect drive, or it won't work. 


1. Is it too much to expect to get a brand new USB drive that has no errors on it?

2. Is there some way to get luksFormat to ignore the bad spots on the drive?

---

### Post by Cryptog on 2007-09-05
btt

---

