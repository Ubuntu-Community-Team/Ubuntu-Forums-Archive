---
title: "/Home and /TMP"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by willieboy on 2008-08-06
I am only using 8.04.1 for a couple of weeks now   but I am making a progress with getting it setup.
I am not dual booting.
There is 1 thing I'm not sure of. The first 2 or 3 times I installed it,  I partitioned the hard drive as 
/ 
(8.04.1   Ubuntu won't accept " /root" in its partition setup.)
/swapfile
/home
/tmp

It all went well, the  home and tmp partitions were OK, that is, they were showing in Places.
I continued to install programs and when they were not right or I made a mistake I formatted & setup the hard drive again.

Then the 2 partitions had the Lost and Found folder in them and I was locked out, I gave myself authorisations but it did not work.

Then the partitions were in "Computer" on the Places menu, FileSystem is in there along with all the other partitions and CD/DVD drives. /Home and /Tmp are in Filesystem along with lots of other folders, I could -and can- access them.
They are in there now with every installation.  I can place them on the desktop if  I want to. 

I have tried different settings and sizes of partitions, also placing /home and /tmp in an extended partition.

Is there (or could there) be a problem with that or is it  OK to use them that way, that is in FileSystem in, I assume Root.

thank you.

---

### Post by spiderbatdad on 2008-08-06
what you have done sounds fine and common...logging in, you are still in user space, so /home/your_username is not a root owned partition. If you run the command ```
id
```You should see uid 1000 (your username)...etc. If you log into your primary user account. You can have others with different uids.

---

### Post by willieboy on 2008-08-08
resolved

---

