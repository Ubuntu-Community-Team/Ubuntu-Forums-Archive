---
title: "New Install - Swap Size"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by _simon_ on 2007-05-13
I have a query!

I returned to Ubuntu yesterday from opensuse. I let the installer do the partitions for me and I've just realised that I now have a 5.8GB swap partition :shock: 

I have 2GB Dual channel 800MHz memory, why on earth would it decide I need such a huge swap space?

What's the best way of reclaiming that space? I'm not even sure I need a swap?

---

### Post by bulldog on 2007-05-13
In your case it's a little over done :) 
If you make a small swap about 500MB it should be more then sufficient.

You can resize your swap and give the space to another partition in front of it or after the swap.
Use the gparted live cd so your hdd isn't mounted.
 [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

But you can install gparted from the repo's and unmount the partitions which you want to resize.
Both should work,but I prefer the live cd.

---

### Post by _simon_ on 2007-05-13
Well that was a bit fo a fiasco but all done :)

---

