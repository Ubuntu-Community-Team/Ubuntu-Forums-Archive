---
title: "Partitioning question"
date: 2006-04-18
forum: Installation &amp; Upgrades
---

### Post by scrook on 2006-04-18
Hi all,

After my hard drive died last night, i'm faced with doing a reinstall of Ubuntu as soon as the new one I ordered from newegg gets in. 

I was wondering what the advantages to having things such as /usr being a separate partition as opposed to having everything under the / partition.

Also I plan to have /tmp be a separate partition as the linux security books that I've been reading highly reccomend doing this. I will make /home it's own partition as well.

That being said, what would be the best way to partition the new drive? (The new drive is 120 gb and it will have a 20 gb windows xp partition (NTFS) and a 40 gb fat 32 partition to act as a common place to put files for both file systems.

---

### Post by aysiu on 2006-04-18
If I had a 120 GB drive (and I do have a 160 GB drive, so it's close), I would do this:

20 GB for Windows (NTFS)
1 GB for swap
10 GB for Ubuntu (Ext3)
89 GB for /home (Ext3)

and use this
[http://www.fs-driver.org/](http://www.fs-driver.org/)

to read/write Ext3 from Windows.

---

