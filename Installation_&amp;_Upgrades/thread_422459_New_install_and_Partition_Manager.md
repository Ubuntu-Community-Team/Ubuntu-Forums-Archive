---
title: "New install and Partition Manager"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-04-25
I am doing a fresh OS install on my laptop, dual boot - XP / Feisty.  I started with an fdisk, installed XP and then Feisty.  

The problem is during the Feisty install when Partition Manager comes up.  It only displays two options.
One is erase and use entire disk.  I don't want to do that.
The other if to manualy set up the partitions.  I don't know how - mount points and all that.

The third option that used to be there - the one with the slider bar where you can just select the relative size of
each partition - is not there.  I have used this same disk on other installs and the option was present but not now.  I even started over with a new fdisk but...nothing.

Any idea why this might be and how do I get that third option back?

Thank you very much.

W-

---

### Post by bhennon on 2007-04-25
Maybe someone can confirm this but i think that the third option you are talking about will appear if you have some unpartitioned space on the drive. 

I just did a dual boot install. i gave 20gb to XP and left 10gb unpartitioned then kicked off the ubuntu install. Then  i had the third option.

I also used the "manual" option and was able to get that up and running. I am no guru so it took me several attempts. To reduce time between attempts. I made a ghost image of my machine after installing XP. I would try different settings using the partition manager and if they hosed my XP install i would simply re-image using the ghost image and start over. Took me three or four attempts. 

I have yet to see a linux partition manager that makes sense to someone that has grown up in the msft environment.

---

