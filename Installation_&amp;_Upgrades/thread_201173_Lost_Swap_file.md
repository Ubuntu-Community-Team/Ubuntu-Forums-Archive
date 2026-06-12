---
title: "Lost Swap file"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2006-06-21
Installed Breezy on new hard drive using 20GB including swap of a 100GB drive. Went into Windows to format remaining space and trashed swap file. Now Breezy  has no swap file. 500MB of RAM and seems to be working OK. Is there a way to repartition a swap file or should I not bother. Going to add another 500MB of RAM also.

---

### Post by rowanparker on 2006-06-21
Do you mean swap for transfering files in between Linux and Windows or do you mean a Linux swap partition?

If it's the first then you can just create another partition.
If it's the latter then you just use mkswap, but 100Gb is far to big for a swap partition.

Rowan.

---

### Post by AllanP on 2006-06-21
[QUOTE=rowanparker]Do you mean swap for transfering files in between Linux and Windows or do you mean a Linux swap partition?

If it's the first then you can just create another partition.
If it's the latter then you just use mkswap, but 100Gb is far to big for a swap partition.

Rowan.[/QUOTE]
It's the second and yes I agree re the size but, that wasn't the case. I had a Linux install created swap file in the 20GB that I gave to Ubuntu (roughly 800MB's). The remaining GB's were to be for Windows backup files etc. It seems to be working ok without the swap; now on 1GB of RAM. Can I make the swap within the Ubuntu partition?

---

### Post by rowanparker on 2006-06-22
> Can I make the swap within the Ubuntu partition? Yes, using [mkswap]("http://www.die.net/doc/linux/man/man8/mkswap.8.html").

Your swap should be double the size of your RAM (well mine is) i think.

Rowan.

---

