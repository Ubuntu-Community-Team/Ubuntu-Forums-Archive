---
title: "resizing partition on fresh install"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2010-06-13
I am running vista and ubuntu 9.04 
I decided on installing 10.04 to increase the size of my Ubuntu partition.

I defraged vista numerous times and then used its disk management to free up all the space it would allow, 8.7gb.

I now have:
Vista  114 gb
Free space  8.7gb
swap 2.1 gb
Ubuntu 26.2 gb
hp recovery 10 gb 

So I start 10.04 install and take manual partitioning. No where can I figure out how to add the free space to the Ubuntu partition. What do I do?

---

### Post by darkod on 2010-06-13
It depends how the space is laid out. If it's how you wrote it, you would probably have to delete the swap and / partitions, also if they were inside extended partition you would have to delete it too.

Then the whole space 8.7 + 2.1 + 26.2 would add together in unallocated chunk of space. From that space create new / and swap partitions, as logical partitions, with the size you want to allocate to them.

---

### Post by Benchrest on 2010-06-13
They are all primary partitions.  I have resolved it as you say. First I deleted swap as I thought it could always be readded. Saw it added to the freespace. Then deleted the / partition. I then reallocated swap and / and installed.

---

### Post by darkod on 2010-06-13
> **Benchrest said:**
> They are all primary partitions.  I have resolved it as you say. First I deleted swap as I thought it could always be readded. Saw it added to the freespace. Then deleted the / partition. I then reallocated swap and / and installed.

I suggested to create / and swap as logical because then they would be together in single extended partition and you would still have option to create another primary later if needed.

Right now, you have used up the maximum of 4 primary partitions and can't create new ones with deleting one. But it's ok as long as you are aware of it.

---

