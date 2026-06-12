---
title: "No &quot;Home&quot; folder listed in gparted?"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by englishmen on 2007-02-23
I'm trying to reinstall ubunt(im using 6.06 live cd) and want to keep my home partition as it currently is, files intact etc. When i get to the partitioning part of the set-up is there suppose to be  a home partition listed? because it only shows a ext3 partition and a swap partition at the end. 

How would i go about clean installing ubuntu but keeping my home folder in tact?

Thanks

---

### Post by taurus on 2007-02-23
I guess you didn't have a separate /home partition.  Therefore, /home is technically under /.  So, you need to backup your /home before you reinstall since it will wipe everything off of /.

---

### Post by Cheizzz on 2007-02-23
Well, as you already stated, "Home" is a folder, not a partition. therefor it does not show up in gparted as a seperate partition. 

/Home is just a folder in your EXT3 partition.
If you format that partition /Home will be gone. 
If I were you I would backup Home and then format and reinstall. 
alternatly, you can try to shrink your EXT3 partition and create a new partition to which you mount /Home.

---

### Post by englishmen on 2007-02-23
I was pretty sure i made a home partition, i guess i did something wrong on that front. My home folder currently takes up 44.8GB and i have  a total of 54.2 free space, if using the live CD i was to resize the current ex3 partition and create a home partition how would i transfer my home folder from one its currently location to the actual home partition?

Many thanks.

---

