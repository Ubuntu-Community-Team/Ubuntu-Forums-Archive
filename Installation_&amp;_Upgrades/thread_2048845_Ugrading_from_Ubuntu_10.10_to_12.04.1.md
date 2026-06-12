---
title: "Ugrading from Ubuntu 10.10 to 12.04.1"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by phamnewan on 2012-08-27
I was doing the Ubuntu upgrades on a regular basis for a while, but got tired of things breaking and I wasn't ready for unity, so I stopped back on 10.10.

Now I want to go to 12.04.1 and have the CD ready to go, but I also happen to have a mirrored RAID (software version).

The RAID currently has 4 partitions.
10GB SWAP
460GB file server
30GB /root
500GB /home

Ideally I would like to use the 30GB raid partition for the 12.04.1, but I have not found a way to make this go smoothly and I admit that I don't want to spend two days putting the pieces back together on this.

---

### Post by Cheesemill on 2012-08-27
There is no direct upgrade path from 10.10 to 12.04, you would have to do 3 separate upgrades:
10.10 > 11.04 then 11.04 > 11.10 then 11.10 > 12.04.
It would be easier to do a clean installation of 12.04 keeping your home and file server partitions intact.

---

### Post by phamnewan on 2012-08-27
What is the best way to do that to a built up RAID?

When I go to do a clean 12.04.1 install, it sees 8 partitions instead of 4.  The only thing I can see to do is to wipe the install partition on 1 disc, put the new install on that and then rebuild the whole thing all over again.

Is there anyway to use the install disc to do a clean install using the current RAID setup?

---

### Post by Cheesemill on 2012-08-27
I think you need to use the alternate install CD.

---

### Post by darkod on 2012-08-27
> **Cheesemill said:**
> I think you need to use the alternate install CD.

+1

The standard live cd doesn't include the mdadm (software raid) package and can't recognize your array.

Either boot in live mode first, add mdadm with apt-get and then click the Install icon on desktop, or use the Alternate CD which does include software raid support by default.

It will show you your MD devices without any problems, and just select the correct mount points in the manual partitioning step.

---

### Post by phamnewan on 2012-08-27
Getting the alternate now.  Thanks for the info, I will let you know how it works.

---

### Post by phamnewan on 2012-08-27
I am installed with 12.04.1 now and most things are working.  :-)

---

