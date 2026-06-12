---
title: "guided - new partition size?"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by superhaus on 2008-02-28
I am setting up a dual boot here.

On the "Prepare disk space" page the guided option has a slider allowing me to set the new partition size. The whole disk is currently in one partition with XP installed. When I move the slider to select the new partiton size, is the number on the slider reflecting the windows partiton or the linux partition?

---

### Post by wolfen69 on 2008-02-28
if you move the slider to 60%,(or whatever) that will be the new partition for linux. make sure to defrag windows first.

---

### Post by forestpixie on 2008-02-28
I thought it was that the 60% (for instance) would be the size of the win partition

---

### Post by wolfen69 on 2008-02-28
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by forestpixie on 2008-02-28
yea - that to me says that there will be 5% of the original partition available for the buntu install

that particular part of the installation is exactly why I get the partition work done before the install and use manual :)

---

### Post by az on 2008-02-28
The slider lets you select a new size for the existing partition. 

The phrase is confusing.  It's not clear whether the "new partition size" means the new size of the partition of the size of the new partition.

For the record, if you put the slider at 60 percent, your original (windows) partition will be resized to 60 percent of the original size and Ubuntu will take the rest.

---

### Post by ugm6hr on 2008-02-28
Why not just use GParted (Partition Editor) from the LiveCD to resize XP manually.  Leave the rest "unallocated" to whatever size you want Ubuntu to take..

Then use the guided - Largest Free Space to install Ubuntu.  That way, there is no doubt about which is which.

---

### Post by forestpixie on 2008-02-28
> The phrase is confusing. - a bit of an understatement :) and I'm glad to see Kirk is boldy back.

> Why not just use GParted (Partition Editor) - which is more or less what I did the first time

- always did find that a bit of a pain, glad to have a bit more of a definitive answer, and if nothing else the OP had been gently introduced to how helpful everyone is :D

---

### Post by motoperpetuo on 2008-03-01
i also find the "new partition size" thing to be really confusing. it should say something like "new partition size (this will be the size of the exisiting partition)." or "new partition (this will be the size of the free space)." whichever it is. i guess i'll know when xubuntu finishes installing here...

i vote that the ubuntu development team make the labeling on this part of the install more specific.

ps: i still love you, ubuntu development team.

---

