---
title: "Swap Space and Second Drive"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by Recked on 2005-03-12
Hello,

I found a post somewhere while googling that mentioned if you had a second hard drive to put your linux swap space on it as it would make your system somewhat faster rather than having the swap on the same drive and the os.

Does anyone know if this is really the case and also how to accomplish this in Ubuntu since when loading the os it doesn't give you the opportunity to put swap anywhere else.

thanks for any help

---

### Post by alastair on 2005-03-12
Make a swap partition wherever you want. In a partitioning program like "fdisk", swap has a partition type 82.

Once made, make the swap signature using "mkswap" - then add to the /etc/fstab file as usual.

Will it make things faster for you on a separate disk/channel? I doubt it.

---

### Post by clparker on 2005-03-12
If you keep your swap file on a separate HDD; a separate physical hard drive than the one the actual OS is running on, it will run slightly faster. It is a technical improvment, but dont expect to see a large perfromance boost. It will make it run better, but not a whole hell of a lot.

---

### Post by bored2k on 2005-03-12
[QUOTE=clparker]If you keep your swap file on a separate HDD; a separate physical hard drive than the one the actual OS is running on, it will run slightly faster. It is a technical improvment, but dont expect to see a large perfromance boost. It will make it run better, but not a whole hell of a lot.[/QUOTE]
 Just dont go making 5gb of swap thinking it will be equal to 5gb ram :P .

---

### Post by Recked on 2005-03-12
Thanks a lot for your answers/thoughts. Doesn't sound like it will do much good. The machine is a dual Athlon processor machine I just wanted to make sure I had things as optimized as possible.

thanks again

---

