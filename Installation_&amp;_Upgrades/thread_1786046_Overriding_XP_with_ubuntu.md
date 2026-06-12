---
title: "Overriding XP with ubuntu?"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2011-06-19
hi all
 i have a dual boot XP pc with ubuntu 10.04 installed.
I don't use Windows XP anymore , as ubuntu has all things i need.. and i was wondering how can i override XP with ubuntu, so that i have plenty of diskspace on my ubuntu..

could anyone assist?

I *guess* as i can mount the windows xp partition from ubuntu, i can just delete every possible file so that i have extra space.... will that do?

w/kindest regards
 marco

---

### Post by YesWeCan on 2011-06-19
Yes, you could just delete all the XP files and be left with an empty, NTFS partition that you can acces with Ubuntu.

What you might prefer to do is to delete the XP partition and then expand the Ubuntu partition to fill the gap. This way you have a bigger Ubuntu partition.

You can do this using a tool called GParted. You cannot expand the Ubuntu partition while you are using it, so you need to do this while booted in a live CD (or another install of linux).

In summary,
Back up any critical data - just in case.
boot off live CD
run GParted in /System/Administration
select and delete the XP partition
select and resize the Ubuntu partition to fill the gap

Have a read of this. I think GParted is pretty easy to learn and this tutorial is excellent: [http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

---

