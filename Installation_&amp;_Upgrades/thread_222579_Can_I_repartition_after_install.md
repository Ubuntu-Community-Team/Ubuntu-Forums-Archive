---
title: "Can I repartition after install?"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Hiroshima on 2006-07-25
I think I made a mistake on install, I partitioned at the prompt, and said 14G for the first drive and 5G for the second.  I thought that this would install Dapper on the 5 and leave me 14 for storage.  I ended up with Dapper on the 14G and 5G for swap.

The question, can I reformat the swap to say 1G (I saw somewhere that I should have 1G swap if I have 512MB RAM - is that right?) and the other four for storage, or should I just reinstall?

Cheers, 

Hiroshima

---

### Post by T700 on 2006-07-25
You have to use the LiveCD to do the partion moving, but yes, it is possible.  Needless to say, back up your data first, just in case!

On the other paw, if I had just installed, I'd probably take the lazy way and pop the disk back in, make a cup of tea, and let it reinstall.  :-)

Paul

---

### Post by jimmygoon on 2006-07-25
You probably want:

4Gig of Ext3 for /
1Gig of Swap /swap
the rest for /shared fat32

maybe?

---

### Post by Hiroshima on 2006-07-25
Yep, Ok I'll give it a go, 4 for home, one for swap and the rest fat32.  Thanks, I'll just stop the updates and start from scratch.

Hiroshima

I don't have anything to update... it's a brand new (to me) computer that was wiped before I got it, anyhow, i'll give it a go.

---

### Post by Hiroshima on 2006-07-25
Zoiks, now it won't boot from CD.  I get a nice little message at the start, (press F12 for boot options) which takes me to a list where I press C for CD, and then it boots from the HD.  Perhaps it didn't do that on the orginal install because the HD was blank... Hmmm I could pull out the HD and try again.

---

### Post by Hiroshima on 2006-07-25
Anyhow, I don't have time to get into a big operation right now, I'll give it a try a bit later, and if I have problems, I'll ask for help again.

Thanks for the information, and the ideas,

Hiroshima

---

### Post by mkw87 on 2006-07-25
Check your BIOS and make sure your set to boot from CD before your hard drive.  That should take care of that problem.

---

