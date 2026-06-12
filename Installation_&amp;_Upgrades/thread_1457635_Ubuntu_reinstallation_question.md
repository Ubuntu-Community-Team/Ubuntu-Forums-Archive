---
title: "Ubuntu reinstallation question"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by fallenashes on 2010-04-18
When installing Ubuntu, I decided to only give it 10 gigs of space, which wasn't nearly enough.  If I do a clean installation will it mess up the GRUB and stop my computer from booting?  (I read that if you just delete the Ubuntu partition your computer cannot boot anymore and becomes a nice brick).

I do not have anything important on Ubuntu, so losing that data doesn't matter.

---

### Post by 2hot6ft2 on 2010-04-18
If you're re-installing it will install grub again so no problem.
If you delete the ubuntu partition then yes all the info for grub is on the ubuntu partition so it wont boot unless you install another boot loader.
Not having a boot loader is far from being bricked though. Bricked is when it's unrecoverable.

---

### Post by fallenashes on 2010-04-18
Well, thanks for the quick response, and glad to know deleting grub doesnt brick.

Will I have 2 linux swaps, or will it overwrite that too?

---

### Post by 2hot6ft2 on 2010-04-18
If you already have a linux swap then don't create another one. It will only use 1.
When you get to the partitioner select manual and click Forward then you can better choose what you want and where you want it.

It will automatically detect and use the one you have.

---

### Post by Josh K on 2010-04-18
Bricking is what happens when you decide to put your computer in a bath to enable "liquid cooling."

---

### Post by 2hot6ft2 on 2010-04-18
> **Josh K said:**
> Bricking is what happens when you decide to put your computer in a bath to enable "liquid cooling."
Sounds like you're speaking from experience.
:lolflag:
Do a search for a thread that's something like
Water cooled have you tried it
or something like that and you'll find an interesting project involving an aquarium and a lot of mineral oil

---

### Post by Jive Turkey on 2010-04-18
You might like to know that its also possible to resize your existing ubuntu partition without having to reinstall.  Boot a live cd, install and or run gparted, use its intuitive interface to shrink the adjacent partition then grow the ubuntu partition, hit apply and leave it alone until it finishes.  If its a laptop make sure its plugged in while resizing the partitions.

---

