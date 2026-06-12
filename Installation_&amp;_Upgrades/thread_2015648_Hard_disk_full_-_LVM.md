---
title: "Hard disk full - LVM?"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by Dave In Sidney on 2012-07-03
I have a 2TB home drive that is getting very full and a spare 1TB drive. The 2 options I'm considering are:
1. Copy several user folders to the spare drive and then mount them on the existing drive; or 
2. LVM

LVM seems to be the best option, but I can't find anything on how to convert existing drives to LVM without losing data. Any pointers gratefully appreciated.

TIA.

---

### Post by darkod on 2012-07-03
I don't think you can convert a disk/partition into LVM without data loss.

I guess the other option is creating a folder (mount point) and then mounting the new disk at that mount point using an entry in /etc/fstab.

---

### Post by rubylaser on 2012-07-03
> **darkod said:**
> I don't think you can convert a disk/partition into LVM without data loss.

I guess the other option is creating a folder (mount point) and then mounting the new disk at that mount point using an entry in /etc/fstab.

You can't convert a drive to LVM without loss.  To the OP, you could use something like [mhddfs]("http://romanrm.ru/en/mhddfs") to present the two drives as /home volume.  In either scenario, you will want to have a method for backing up this data if it's at all important to you.

---

