---
title: "Replacing OpenSuse with Ubuntu without Formatting and Loosing Data"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by bineeshm on 2008-07-05
Hi! All

I'm a new migrant to Linux world and trying to learn things here. But I'm kind of over enthu and tries too many things without much knowledge. Now I've got a couple of question and hope someone can help me on these.

1. I've Ubuntu Hard installed in my system. If I have to replace it with OpenSuse or vice versa (no dual boot) should I do a fresh installation?

2. (Another version of above query) Is there a way I can overwrite one distribution with another without loosing data. For example, if I my system runs on OpenSuse and wants to replace it with Ubuntu. I install Ubuntu on top of OpenSuse (I dont know how, trust someone would help me here) and when I restart system next time, I want to see Ubuntu running and no previously saved data was lost, no change in partition.

The queries might be lil stupid, but I'm really looking whether it can be done. Any help/guidance would be lot helpful.

Cheers!!

P.S: Can someone direct me to some resource where I can learn better about Linux partitions and how to edit them. Linux partitions are really too much for a long time Windows user like me.

---

### Post by Sealbhach on 2008-07-05
When you're installing, if you create a seperate partition called /home then you can upgrade without losing data. You install the upgrade on the / partition. 

I don't know if it works if moving from one distro to another though.

There's some info about partitioning here... with some links.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I was a bit scared of partitioning too but it's not too bad. Be careful to back up anything precious though.

 
.

---

### Post by bineeshm on 2008-07-05
Hi! Swalbhach,

Thanks for the response. I'll try your recommendation. However, I still has a question, if we already have a /home in the existing system wont it clash with the new partition?? (I someway feel Windows partition was easier to understand C:, D: is much simpler than /, /home/ ext2 ext3 and all)

Cheers

---

### Post by Sealbhach on 2008-07-05
> **bineeshm said:**
> Hi! Swalbhach,

Thanks for the response. I'll try your recommendation. However, I still has a question, if we already have a /home in the existing system wont it clash with the new partition?? (I someway feel Windows partition was easier to understand C:, D: is much simpler than /, /home/ ext2 ext3 and all)

Cheers

If you do a manual partitioning

Choose manual at this screen here

[img]http://www.psychocats.net/ubuntu/images/installinghardyplus11.png[/img]


 you can tell the partition manager e.g Gparted, which partition you want to use as the root partition (/) and which which one you want to use as /home folder. So if you tell it that you want to use your existing /home folder as the /home folder in the new installation, it will leave all the files and data in the /home folder unharmed.

Don't forget that Ubuntu also creates a small swap partition to use as memory overflow if needed.

Use partition type ext3 for / and /home. Use swap partition type for your swap partition.

Just make sure you have all your precious files backed up, then you can be free to experiment and even make mistakes, that way you'll learn even better.:)


.

---

### Post by bineeshm on 2008-07-07
Thanks much, buddy. Actually I learned Windows by Trial & error in college systems. Now I dont have access to those many systems to play around other than my Laptop :(. Still, I'll play around more and try learning Linux.

---

### Post by zvacet on 2008-07-07
@ **bineeshm**

To answer your original question:

1.yes

2.you can do that if you have separate home partition,but in that case I will save just my data and files.You may have problems if you try to use settings from rpm based distro (OpenSuse) to deb based distro (Ubuntu).

---

