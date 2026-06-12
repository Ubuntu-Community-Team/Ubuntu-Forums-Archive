---
title: "Ubuntu 9.10 on Intel SSD"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by NMZmaster on 2009-11-13
I recently purchased a second generation X25-m series SSD from Intel, and was planning to use it as my boot drive with a clean install of 9.10.

Is there any reason why this would be a bad idea, or perhaps any tweaks that I should do to make 9.10 more SSD-friendly?

---

### Post by earthpigg on 2009-11-13
i think it would be a great idea.

indeed - my primary hard drive on my primary desktop is an SSD.

i haven't done anything to make the OS more 'ssd-friendly'.

i think the hype about SSD's failing due to frequent writes is blown out of proportion at the behest of vendors of conventional radial hard drives. even the ones that do make SSD's still have tens of thousands of radial hard drives in warehouses - once those are sold, "revolutionary new technology" will be announced that makes SSD's able to handle frequent writes without damage. in reality, the only thing "new" will be that the warehouses are now empty of obsolete radial hard drives.

***all*** hard drives eventually fail as a result of continued use, not just SSDs.


i have a plain-jane linux install on my SSD, zero modifications. also zero swap space, because the hard drive itself has less storage space.

---

### Post by NMZmaster on 2009-11-13
Alright, thanks for the information!  Looking forward to getting 9.10 on my desktop (though I've used it on my laptop, the desktop has been running 8.10 for about a year now and a clean install should be nice).

---

### Post by madsc89 on 2009-11-13
I am running on a first gen Intel x25-M 80 GB. I dual boot Ubuntu Karmic and W7 atm, and have asked this question some times on this forum before...
I think the best place to go for any beneficial tweaks is the OCZ forums.
One tweak that is bound to add some performance is the noatime setting. It basically disables the wait-for-access-time-feature which is good on HDDs, but not on SSDs.
Also the IO scheduler could be altered. See why and how in the OCZ forums.
I've also aligned the partition to match erase blocks, but I'm not sure if I did it correctly. It is literally impossible to find any definite answer on what settings s best for the Intel SSDs. I used 512 bytes per cylinder (I think), as described here: [http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)

You should do the aligning bit before you install anything! It's a bit risky. I did it, and broke my W7 partition, barely managing to fix it (but I did). Just create your partitions using fdisk, then install on them.

EDIT: Typos.

---

