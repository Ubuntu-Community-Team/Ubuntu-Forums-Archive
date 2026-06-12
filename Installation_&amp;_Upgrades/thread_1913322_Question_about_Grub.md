---
title: "Question about Grub"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by jalberro on 2012-01-22
Hello! Yesterday my HP notebook die and the oficial service restore my original OS using the Recovery Boot and after that my grub of Ubuntu 11.10 disappear.

My question is, can I restore the grub using a Live CD from Ubuntu 6.0? It's compatible? I don't have a new version where I am now.

Thanks a lot!

---

### Post by abhijeet.1308 on 2012-01-22
I think it's not possible.
   when you use original OS the the windows boot loader is get install which doesn't allow you to boot any other OS   so i suggest that you should replace your boot loader first,then install your any other OS.

---

### Post by darkod on 2012-01-22
With a 6.0 CD you can't install the grub2 for 11.10. It's a newer version.

But that's not your main problem. If they did a factory restore you might not even have the ubuntu partitions on the disk. So restoring grub might be pointless, in fact it might not boot at all with grub2 on the MBR.

If you open Disk Management in windows, can you see any undefined partitions on the disk? I say undefined because windows can't recognize fully linux partitions.

And try to get a newer ubuntu cd as soon as possible. You need to have one, it's very useful.

---

### Post by jalberro on 2012-01-22
Thanks to both for the replies!
I'll download the 11.10 version and "burn it" into a USB drive. I'm not in my town, that's why I don't have a newer version.

Thanks again and I'll keep informed! :)

---

