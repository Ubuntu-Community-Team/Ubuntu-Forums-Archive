---
title: "Refit stuck at tux logo, will not boot on mac"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by peruvianfreak250 on 2010-01-22
Hi, i have a new macbook pro that already dual boots windows 7 and mac os x. I've tried to put ubuntu on the last partition and installed grub .97 instead of grub 2, because refit doesn't like grub2 and recognizes a partition with grub2 as legacy os instead. So i have everything installed correctly but when I try to load ubuntu i just get the tux logo in the middle of a grey screen and the computer hangs there, and i have to manually shut down. I've tried the boot up and shut down trick and it doesn't help. What do i need to do?

Thanks

---

### Post by quixote on 2010-01-23
(Maybe a mod could move this to the Apple Users section?  Better chance of a good answer there.)

Since tux-logo-on-gray-screen is refit, not grub or ubuntu, my guess would be that refit isn't pointing to the right partition.  I.e. it tries, but there's no ubuntu there.  ??

---

