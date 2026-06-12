---
title: "Partitioning - how do I know which drive is C:\ and which is D:\ ?"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by eddy147 on 2008-11-24
Hi Aysiu,

I have 1 disk, 2 partitions (C and a D drive).
On C I have Windows XP installed.

I've seen in tutorials how to make a dual boot, which I dont want, or use the entire disk for Ubuntu, which I dont want either.

I want to keep all my data on D, but replace Windows for Ubuntu.

I dont know how to do that....
C and D drives have the same size. So I do not recognize them in the installation step.

Do you maybe some resource where I can get information to make this install possible (maybe yours?)

Thanks in advance,
eddy

---

### Post by Sammi on 2008-11-24
> **eddy147 said:**
> Hi Aysiu,

I have 1 disk, 2 partitions (C and a D drive).
On C I have Windows XP installed.

I've seen in tutorials how to make a dual boot, which I dont want, or use the entire disk for Ubuntu, which I dont want either.

I want to keep all my data on D, but replace Windows for Ubuntu.

I dont know how to do that....
C and D drives have the same size. So I do not recognize them in the installation step.

Do you maybe some resource where I can get information to make this install possible (maybe yours?)

Thanks in advance,
eddyI'm guessing the problem is that the Ubuntu installer is referring to your two partitions as sda and sdb, in sted of C: and D:, as your used to from Windows. And that neighter partitions as a "title" and are maybe just referred to as "unnamed". In all likelyhood C: should become sda, and D: something after that, like sdb or sdc.

But you need to doublecheck before you format and overwrite anything.

Here's a noobish way I would use to find out:
I am fairly sure that if you're using the Live CD for installation, you should be able to access both partitions through the file manager. If so then try opening the partition manager from system -> administration (again I'm only fairly sure it's there, it may be somewhere else in the menu, just look for the word "partition"). It should tell you the Linux device names of your partitions (sda, sdb, sdc, and so on), and where they are mounted. The mount names in the partition manager are the same as the mount names of the partitions when you look the up in the file manager, and by checking what content is on both partitions, you'll figure out which is which.

Hope this is what you're looking for.

---

