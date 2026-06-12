---
title: "OMG Deleted partition table!"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by mozz on 2005-07-17
Ok guys...I've done a whole lot of bullshit in my life, but that's the top of the mountain:

Tried to delete the Partitions on my external hd (sde1) but instead of this I deleted the partitions on my old windows system (hde1) AND the external sde1...best thing about this: sde1 was the backup of hde1

Is there a way (a program?) to recover the partition table (from the external or the internal hd doesn't matter)? Please, please help me...

I think I've found one way to make a man cry (yeah.. even such a dumb one)

---

### Post by tomchuk on 2005-07-17
So did you delete just the hde1 partition, or all partitions on hde? What filesystem was on hde1 (and other hde partitions), was there more than one partition?

---

### Post by mozz on 2005-07-17
thanks for answering!

there was one primary (ntfs, hde1) and one logical with a ntfs an a fat32 partition...i deleted them one after one in gparted..

is there any hope?

---

### Post by bored2k on 2005-07-17
[QUOTE=mozz]thanks for answering!

there was one primary (ntfs, hde1) and one logical with a ntfs an a fat32 partition...i deleted them one after one in gparted..

is there any hope?[/QUOTE]
 I would suggest using a recovery disc like UltimateBootCD or Hiren's Boot CD, wich have some awsome recovery tools for this type of things. It doesn't always work though.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) UBCD has Active Recovery and a myriad others.
[http://www.partition-recovery.com/](http://www.partition-recovery.com/)

(Hiren's is kind of shady so I won't link, but its the one I use)

---

### Post by tomchuk on 2005-07-17
All you need is [TestDisk](http://www.cgsecurity.org/index.html?testdisk.html)
Edit: or [gpart](http://www.stud.uni-hannover.de/user/76201/gpart/)

---

### Post by chaumurky on 2005-07-17
[QUOTE=tomchuk]All you need is [TestDisk](http://www.cgsecurity.org/index.html?testdisk.html)
Edit: or [gpart](http://www.stud.uni-hannover.de/user/76201/gpart/)[/QUOTE]
 Most importantly (probably obvious but has to be said), DONT WRITE ON THE DISK until you've recovered.

---

### Post by mozz on 2005-07-18
Thank you all...so much, everything is like it used to be in the ol'days- the system disk as well as the backup disk

(Rescued it with testdisk)

Like B.B. King said: I'm sooo glad...thanks again

---

