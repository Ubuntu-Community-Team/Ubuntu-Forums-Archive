---
title: "installation help, dual boot Ubuntu/XP"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by squivo on 2005-09-23
After partitioning my hard drive I am ready to install Ubuntu on my new lappy.  I am also running XP, and I wanted to know before I just run default install if that will wipe my partitions, trashing XP.  DO I have to custom install if I wan to keep XP safe and sound?  What are the steps I should take?

---

### Post by aysiu on 2005-09-23
You need to follow these directions, especially #3:

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

Then install Grub to the MBR.

---

### Post by squivo on 2005-09-23
Thanx... that's a good link.  The installation guide for Ubuntu should have pictures with it.  I slowly figured it on my own and everything seems to be working okay so far.

---

### Post by Herman on 2005-09-23
Here's a new site that might not be too well known yet:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) 
 It contains illustrations of what a typical dual boot install should be like.
 I just made it myself and I hope it will help people.
If any moderators disapprove of it I will remove it right away.

---

### Post by dosed150 on 2005-09-23
nice site i havnt got my disc yet but i know ill be using your site to help with my install when it comes

---

### Post by cotcot on 2005-09-26
If you want to set up a dual boot XP/Ubuntu it is good to consider making a partition with a file system where as well XP as Ubuntu can write on (for instance FAT32). This makes it easier to share data with the two operating systems. Ubuntu can read NTFS (XP) file systems but cannot write on it (actually it seems to be possible but the way to do is not advised for the average user).

---

### Post by Herman on 2005-09-26
[QUOTE=cotcot]If you want to set up a dual boot XP/Ubuntu it is good to consider making a partition with a file system where as well XP as Ubuntu can write on (for instance FAT32). This makes it easier to share data with the two operating systems. Ubuntu can read NTFS (XP) file systems but cannot write on it (actually it seems to be possible but the way to do is not advised for the average user).[/QUOTE]
    Thank you for your excellent advice, cotcot, I agree with you! I have plenty of empty space left on the website;     [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

 Showing how to create a fat32 partition as you suggest, would be a good way to further demonstrate the use of the partitioner and achieve something useful at the same time. I could keep it seperate and call it 'part two' or something like that, so as not to confuse the new ubuntu enthusiasts too much. Then they can then advance to that in their own time, when they are ready for it.

    I will start on it right away, but I do not know how long before I will be ready to update the website. In the meantime your post will help a lot of people by making them aware of the fact that they can do that.

---

