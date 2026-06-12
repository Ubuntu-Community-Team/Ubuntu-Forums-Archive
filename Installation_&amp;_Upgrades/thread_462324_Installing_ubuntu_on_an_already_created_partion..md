---
title: "Installing ubuntu on an already created partion."
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by SmoshySmosh on 2007-06-02
I just reformatted my PC a couple days ago, and made 6 partitions out of my 2 drives, one partition mainly for Ubuntu, But since I already have the 6 partitions on my PC will I still be able to install Ubuntu on to that one I made for it without any problems?

---

### Post by fsando on 2007-06-02
That's what I've done more than once.
I created partitions and then I just went through the installation and when it shows the partition menu I went for 'manual'. It recognized all the partitions so I just had to assign mount points like '/', 'home' etc. 
It offers you choices to to choose from - you don't have to write anything yourself. 

It may ask for you to create a 'swap' partition (then create one that is 50% larger than your memory).

Another route is to give it a full partition to do with what it wants. Then it creates the different 'mount points' itself.

I created two partitions specifically because I wanted my 'home' folder to be on a partition of its own.

As for "without problems" you should be ok but one never knows ;)

---

### Post by SmoshySmosh on 2007-06-02
But since I already have 6 partitions wont that complicate things? I thought 6 was the max.

---

### Post by fsando on 2007-06-02
From old knowledge I think you have a limit of 4 primary partitions pr. harddisk one of which can be an extended partition. What you do then, is to create one extended partition. On this partition you can create many (I don't know how many) logical partitions. So I guess that some of your partitions are on an extended partition (if you have only one hd).

I'm definitely not an expert but I think you need to boot linux off a primary partition. I only know from my own experience that my '/' is on a primary partition and I have continued to put it on primary in later installations.

ADDED:
If you let the installation handle one entire partition - it will not partition it further (except perhaps for the swap partition which will be invisible from the users perspective) it will just create the folders.
The reason for having certain folders on different partitions is the same as in windows: convenience of update, backup etc.

---

### Post by SmoshySmosh on 2007-06-02
Well. I am on the live CD now trying to install it, but it gives me that error to make a swap disk, how do I do this out of my one partition I set aside for it? I am so stumped. Will it make the swap disks if I just continue?

---

### Post by fsando on 2007-06-03
I think the easiest in your case is to choose manually create partitions and create the swap partition yourself.

If you see the visual partitioner:
(I just tested this - didn't go all the way with it, though, as I just installed yesterday).
Resize the partition you want to use and and  create a swap partition in the rest of that space. I think from my previous installs that your swap space should be approximately 50% larger than your memory (probably no harm in making it bigger - though the extra space is likely never used)

If you see a text based interface:
I think you may have to delete the partition in question (I didn't see a 'resize' option), recreate it a little smaller and then create the swap partition in the rest of that space. This is exactly what I've just done yesterday on my old laptop.

Hope this helps. 

Oh btw. do you have important content on the other partitions? If so you should definitely make backups. 
When it comes to messing with the harddisk anything may go wrong (and as as stated in Murphy's law 'anyting that can go wrong will go wrong' ... eventually.)

---

