---
title: "Hiow to create a partition for ubuntu"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by voodoo_child on 2008-04-30
Hi,
This is my current filesystem:
[http://i11.photobucket.com/albums/a170/vairish/Screenshot.png](http://i11.photobucket.com/albums/a170/vairish/Screenshot.png)

The 60Gb partition on the left is my Vista one. The 66Gb one on the right is my 'data' partition (music etc). 

I want to use the unnallocated one on the middle (20.53Gb) for my Ubuntu install. 

But the guided installer doesnt seem to want to; it keeps trying to mess with my Vista partition, which I don't want to resize. I just want to use the 20Gb partition and nothing else. Even if I go to 'use largest free space', he still wants to mess with my Vista partition instead of using that 20Gb one. 

So my other option is the manual partition install thinger. But I don't know how to do this - it keeps telling me 'no partition table' or some such. 

Can someone help me with a step by step - what file system to use, swap files etc.? How to get everything ready so the Ubuntu will install onto it? 

Thanks

---

### Post by voodoo_child on 2008-04-30
I got bored waiting for help, so I randomly stabbed at buttons and figured something out. 

Thread closed

---

### Post by Rallg on 2008-04-30
That explains why my detailed reply was rejected by the forum.

---

### Post by voodoo_child on 2008-04-30
I don't know anything about rejected posts, but if you took the time to reply, thanks. 

I got it figured in the end, just wasnt sure what partitions i needed to create and what filesystem they should be. I created a 16Gb ext file (or something) and 4Gb swap file. Whatever options I selected, anyway, it let me continue and im in the Ubuntu environment now. 

There's horrendous performance though.. the system monitor is showing both my processors (T7500) near maxed all the time, but nothing in the processes list is using more than 1 or 2%. I must have screwed up the partitions or something. 

Bugger

---

