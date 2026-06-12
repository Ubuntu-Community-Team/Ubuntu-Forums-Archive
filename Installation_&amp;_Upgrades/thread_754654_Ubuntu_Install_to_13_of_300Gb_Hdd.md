---
title: "Ubuntu Install to 1/3 of 300Gb Hdd"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by jqball2u on 2008-04-14
I bought a 300Gb IDE hdd, partitioned it into 3 100Gb (approx) partitions and installed windows XP on one, Vista on another and Ubuntu on the 3rd.  I have 2.4 GHz Dell, with 1 Gb RAM.

What are the sizes I need for the root, swap, and home partitions?  I updated my system and then tried d/l-ing some programs via synaptic package manager and about 2/3's of the way thru, it tells me it couldn't find enough space!?  Does ubuntu use more space on the root partition to install programs or the home partition?

Linux programmer's need to universalize that, the partition requirements ... I know some Linux' distro's use the root to install programs and the home for doc's, pix, music, video's, system setup info, etc.,  while other Linux
 distro's use the root just for the operating system only and the home for all the rest (including programs).

Thanks ya'll,
QBall

---

### Post by PmDematagoda on 2008-04-14
Please post the output of:-
```
df
```

---

### Post by jjk7288 on 2008-04-14
Personally, I'd make sure Ubuntu has enough on its primary partition to run comfortably, probably no smaller than 10 gb and you should get by, but it depends how much you install. You don't *need* a seperate home partition, it's just nice to have if you ever have to reinstall, so if it's really an issue you could put them on the same partition. Packages I believe are never installed in a user's home directory, and if it's possible I'm sorry to say that I don't know how.

That being said, if you insist on having a home partition, it can be any size, just so long as it fits all of your Linux documents/settings/etc. The root partition is primarily for installed programs, though some programs can be installed in your home directory if it has an installer that gives you options (i.e. not packages)

Swap partition is generally recommended to be about twice the size of your RAM, but I always say no less than 4GB.

---

### Post by SnakeHips on 2008-04-14
Just for example on  a 160G drive my install is as follows

/ = 10G less than 1G used ;-)
/swap 0.5G its never used more tha 8% ??
/usr 5G where i believe programs are installed - 2.5G used
/home 50G where i keep all my stuff - and backed up to an "old" drive

and the rest is spare...

hope it helps

---

### Post by mikewhatever on 2008-04-14
> **jqball2u said:**
> 
What are the sizes I need for the root, swap, and home partitions?  I updated my system and then tried d/l-ing some programs via synaptic package manager and about 2/3's of the way thru, it tells me it couldn't find enough space!?  Does ubuntu use more space on the root partition to install programs or the home partition?

Sizes may differ depending on one's needs. How large is you root? Can you post the output of <df -h>.

> Linux programmer's need to universalize that, the partition requirements ... I know some Linux' distro's use the root to install programs and the home for doc's, pix, music, video's, system setup info, etc.,  while other Linux
 distro's use the root just for the operating system only and the home for all the rest (including programs).

Really?

---

