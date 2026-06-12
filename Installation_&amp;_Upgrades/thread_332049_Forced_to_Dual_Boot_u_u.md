---
title: "Forced to Dual Boot u_u"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Riyonuk on 2007-01-05
It seems I am forced to dual boot in order to have a working internet connection. If I just install Ubuntu internet never works, if I install windows then ubuntu it works fine. Why is this?

Also, I cant seem to install windows and ubuntu, I install windows and then when installing ubuntu I resize windows to 2GB and 58GB to Ubuntu and 2GB to swap. Everything seems to be working fine, I try to boot into windows and I get the following error 

Error 24: Attempt to access block outside partition
Press any key to continue...

So I'm thinking to myself, well its probably to small of a partition, so I re-do the whole process again, and this time make windows 5GB...no luck.

So I go 2GB, 5GB, 10GB, must I go to 15 in order for it to work? Am I doing something wrong when partitiong? Does it have to do with the "Would you like to set the ubuntu partition at the End or Begining", whatever that means...

---

### Post by bulldog on 2007-01-05
If you're running ubuntu,your windows install has nothing to do,so if you only have a connection with windows installed,it should be an ubuntu error.

Do you have a connection with the live cd?

What about your partitions trouble,download the gparted live cd ,

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn it to a disk and boot from it.
See if there are any errors listed,or if there's no data on it,repartition it again and see what happens.

---

### Post by Riyonuk on 2007-01-06
Well, it "seems" that if I have windows and ubuntu installed, internet works fine on both. If I have just ubuntu installed, it takes time to get it working.

Does Ubuntu have a "Hold on, Connecting to Network" dialog? And Ill try that gparted cd tonight.

Last question, I guess I formated, and when I started up my new ubuntu, it had items in the trash, so I looked and they were items I deleted 2 installs ago, am I not formatting?

---

### Post by bulldog on 2007-01-06
Do you have a separate /home partition?

Not very familiar with the networking thingy,never had probs with it.

---

### Post by Riyonuk on 2007-01-06
No, I dont. What I do is give 58.0 GB to Linux and 2.1 GB to Swap.

---

