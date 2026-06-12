---
title: "Shrinking Vista with Gparted is really dangerous?"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by ehdtkqorl123 on 2007-12-02
I am planning to shrink Vista and expand Ubuntu drive.. But there are some arguments saying that it is really dangerous to shrink Vista using gparted... some ppl says yes but others say no..
So if I am gonna shrink Vista, how should I do it? Do I go to vista and shrink the vista hard drive space? - Is this possible?
If so, after shrinking vista space I will have some spare space.. Then can I expand ubuntu space to merge this spare space? I am wondering if what I said is technically possible..

It sseems it is the safest way to shrink vista partition on Vista - using hardware manager or some function(can't remember the exact name). 

Am I right?

---

### Post by merlinus on 2007-12-02
vista has its own disk manager, which can shrink its partition.  It is best to use this, as vista maintains some kind of dynamic partition sizing.

Then you can use gparted live cd, or perhaps the one on the ubuntu live cd, to grow your linux partition into the freed-up space.

---

