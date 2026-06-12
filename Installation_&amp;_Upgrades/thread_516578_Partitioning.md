---
title: "Partitioning"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by OMRebel on 2007-08-03
Hey guys, I just got a new laptop (Dell 1501), and want to setup a Dual Boot on it.  I want to give Ubuntu 35 GB on my drive.

Going through the install on the CD, I get to the point where I need to create the partitions, and not real sure what I should select.  I'm attaching a screen shot to this post.  Any help would be much appreciated.

---

### Post by LaRoza on 2007-08-03
Can you tell us more?

It looks like you have Vista, but what is that FAT16 partition doing there?

---

### Post by loserboy on 2007-08-03
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

just click new partition and make it the size you want and choose ext3 for the FS type, the link should give you a good walkthrough but let me know if you get stuck

edit: the fat16 is something that Dell does, it's on mine too just ignore those

edit again: sda2 is your backup image you dont want to mess with that one, you want to make free space on sda3

---

### Post by OMRebel on 2007-08-03
Thanks everyone.  Can't wait to see how Ubuntu performs on this laptop!

---

### Post by OMRebel on 2007-08-03
So in my case, I change the mount point to just "/" or leave it as "/media/sda3"?

---

### Post by loserboy on 2007-08-03
well if you want to dual boot, in simple terms you are going to split that sda3 in 2  and leave the original half (with xp on it) alone mounted as /media/sda3 ( or you could rename it to /media/xp)

then you call the new part "/"  

also you're gonna need a swap partition


some people like to have seperate /home partition, but since this is your first time don't worry about it, we'll just keep it simple

---

