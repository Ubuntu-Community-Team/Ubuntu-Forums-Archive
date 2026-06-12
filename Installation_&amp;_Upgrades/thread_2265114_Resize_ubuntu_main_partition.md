---
title: "Resize ubuntu main partition"
date: 2015-02-12
forum: Installation &amp; Upgrades
---

### Post by Paul_Cambal on 2015-02-12
Hello everyone,
I've already messed up with partitions, so now im afraid of touching anything. I'd like to reduce the size of ubuntu on my hard drive. I thought about using a gparted live version of linux, then resize the mount point (that's how / is called, isnt it?) of the currently installed ubuntu partition. I've read this article about this: [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)
It should be data-loss free, and I dont have to resize or move any other partitions (swap and co), right?
Thanks for helping me out :)

---

### Post by yancek on 2015-02-12
It would be helpful if you could post an image of the GParted screen showing your partitions.  Do you only have the Ubuntu / partition and swap?  Without more details, there is no way to give specific advice but using GParted on a Live CD is the best way and any time you are changing partitions there is a possiblity of data loss.   The link below is a very detailed tutorial on GParted and Section 6.B specifically explains resizing.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Paul_Cambal on 2015-02-13
[IMG]http://i.imgur.com/p6IYO7f.png[/IMG]
From left to right:
-Windows recovery environment ( I'd better not touch it)
-Windows 7
-What I call main partition (/)
-You guessed it, /home and swap
-some unallocated space

The reason why I want to shrink /'s size is because I want to install elementary os, which requires 700mb space. 
It doesnt need its own /home and swap partitions, as its meant to be usable as a live image, right?
Thanks all :)

---

### Post by Bucky Ball on 2015-02-13
Don't know anything about Elementary, but if based on Ubuntu, it will use the /home and /swap you already have if you install it, choose 'Something Else' and mark those existing partitions to 'Use' but NOT to format. 

ALWAYS back up any valuable data prior to resizing or tweaking partitions. As yancek suggested, boot from the Live install media (USB or disk) and use Gparted to resize /. Good luck and fire away if you hit a brick wall. As you have a separate /home partition, you could probably split your current Ubuntu install partition in half for Elementary. I never use more than 15Gb partitions for Ubuntu and its flavours, but I have separate data partitions, too. ;)

PS: If you are going to use Elementary 'live', why do you need to make space to install it on the HDD at all?

---

### Post by Paul_Cambal on 2015-02-13
I mean elementary is meant to be live right? I just want it to install it on my hdd, thats why I'd like some space freed!
Also, thank you all, this took a while, but Gparted finally resized /'s partition, I now have 5Gb freed :)
I'm gonna have to look for an elementary installation guide now..
Thanks again everyone who helped me ;)

---

### Post by Bucky Ball on 2015-02-13
Good news. Please mark as solved by following the second link in my signature to help future travelers and feel free to post somewhere [here]("http://ubuntuforums.org/forumdisplay.php?f=447") for any support with Elementary. Good luck. ;)

---

### Post by tokyobadger on 2015-02-13
elementary is based on ubuntu so the minimum of 8Gb still holds for an installation - I'm not sure that 5Gb will be enough. Swap can definitely be "recycled", as for /home probably but depends potentially on what version of ubuntu and what version of elementary

---

### Post by yancek on 2015-02-13
You are using an MBR system and you already have 4 primary partitions created, the two for windows, the Ubuntu filesystem (sda3), and an Extended partition (sda4) which is very small and although you could create another partition there, you don't have enough room to install Elementary.  I don't see how it would work.

You could move the /home partition (sda5) to the Ubuntu partition and install Elementary on sda5.
You could also install VirtualBox on either Ubuntu or windows and install Elementary there.

---

### Post by Paul_Cambal on 2015-02-13
Elementary only needs, 4,4 gigs, also, I've created sda7 underneath sda4, and it works fine, im currently writing from my brand new os ;)
Thanks again

---

