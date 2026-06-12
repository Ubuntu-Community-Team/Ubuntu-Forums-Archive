---
title: "Xubuntu installtion"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by steliosgr on 2008-04-16
hi all.
I have ubuntu at my home and everything its ok. I like linux very much and i decided to installed at my office.

I downloaded xubuntu 7.10 booted from live cd and runned installtion.

My question is... my office pc have a HDD with windows xp profesional.
at partition tab in xubuntu setup what i must choose to have windows xp and xubuntu together?

The HDD is 40GB and i want 10GB only for linux. 
I must resize the ntfs partition to 30 GB and use the other 10GB like 1GB for swap and the 9GB fro "/"?

If i resize the 40GB NTFS i will lost windows XP?

---

### Post by Partyboi2 on 2008-04-16
> I must resize the ntfs partition to 30 GB and use the other 10GB like 1GB for swap and the 9GB fro "/"? Yes, use something like [gparted]("http://gparted.sourceforge.net/") (I think its on the xubuntu live cd under Applications->System->Gnome Partition Editor) to resize your windows partition, then when you get to the partitioning part of the install choose manual and create a 1 gig swap and 9 gig / root
>  If i resize the 40GB NTFS i will lost windows XP? 	If you have 10 gig free on the 40gig drive you should be fine to resize it to 30gig and leaving 10 gig for ubuntu. But I suggest backing up your important stuff to be on the safe side.

---

### Post by steliosgr on 2008-04-18
Thank you.

---

