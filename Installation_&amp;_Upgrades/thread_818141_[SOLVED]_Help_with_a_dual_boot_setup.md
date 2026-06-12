---
title: "[SOLVED] Help with a dual boot setup"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by swedishlightning on 2008-06-04
Hi all,

I have been running ubuntu 7.10 off an external USB drive for the past 6 months or so, and am finally sick of lugging the thing around with me whenever I want to boot into linux. At this point I want to wipe my internal drive and start from scratch with a dual-boot system running ubuntu and XP.

My internal drive is 80GB and at this point a vast amount of it is consumed by music, videos, etc. so my question is: Can I create 3 partitions, one for ubuntu and one for XP (each around 10GB), and then one that holds all the media files that I can mount in which ever OS I happen to be using. 

OR 

Is there a better way to accomplish this "file-sharing" setup since all I really want is to be able to play music in each OS without having duplicates (my harddrive couldn't fit it all twice anyway).

I have never really done any partitioning before so my question may have an obvious answer. In any case I appreciate any input you might have.

Thanks,

Thatcher

---

### Post by bobblehat on 2008-06-04
You should be able to do this OK. One way would be:

Install XP first (just because the Ubuntu installer does a better automatic job of handling the fact that you already have an OS there). Create yourself a couple of partitions via the XP installer, one for XP itself, one for your data and leave some spare for Ubuntu (make your own choice on size but a gut-feel guess would be 10GB per O/S is OK as you suggest and the rest for data).

Now install Ubuntu and select the 'guided - use free space' option in the partitioner.

You should now have a dual-boot XP/Ubuntu with a Grub menu and be able to access/mount the data partition in either.

---

### Post by swedishlightning on 2008-06-04
Thanks for the reply!

I am now running my new XP install and as soon as I finish setting it up the way I like, I'll throw in the Ubuntu disc and get that squared away.

Thanks a ton for you help, it worked exactly as you said.

Thatcher

UPDATE: I have everything installed and its all working great! Thanks again.

---

### Post by bobblehat on 2008-06-05
No problem - and thanks for the updated to mark it solved.

---

