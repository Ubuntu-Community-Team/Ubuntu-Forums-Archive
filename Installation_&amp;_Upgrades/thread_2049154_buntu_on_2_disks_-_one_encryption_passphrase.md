---
title: "*buntu on 2 disks - one encryption passphrase?"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by DiagonalArg on 2012-08-28
Installing ubuntu on two disks.

I want swap & root on md1 (more redundancy), backup on md2 (less redundancy).

I want to encrypt both md1 & 2, but on boot I only want to input a single encryption passphrase.

I do not want to combine md1 & 2 into a single LVG, since that will not allow me to specify that swap & root go on md1 & backup on md2.

Any way to do it?

Thanks
/DA

---

### Post by wirelessmonkey on 2012-08-28
I can't speak authoritatively on this, but I have a separate disk that is encrypted the way you describe. It's been almost a year since I did it so be sure and test! 

Before creating my LUKS volume, I mounted the second disk on disk 1's filesystem. That's all it took, IIRC, though I could be mistaken.. 

Just remember that your boot partition CANNOT be encrypted if you expect it to actually boot the system.

---

### Post by DiagonalArg on 2012-09-11
wirelessmonkey - I'm traveling & just got your post, now.  I'm not exactly sure how to do that mounting using the partitioner during the install process, so if you have any wisdom to share on that score, please do.  In any case, when I get home in a couple of weeks, I'm definitely going to look into it.

Thanks,
/DA

---

