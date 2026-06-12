---
title: "Dual-Boot Installation / GParted / Space Preceding?"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by usersock on 2010-07-12
I'm following this [Lifehacker guide]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony"), trying to install both Win7 and Ubuntu. The guide is having me use GParted to partition space for Ubuntu. I'd like to give 20 gigs to Ubuntu, 80 gigs to Windows 7, and the leftover 198 gigs will be used as storage on it's own drive. 

In GParted, I need to set a number (in megs) for "Free space preceding", but I have no idea what that number should be. The 80 gigs I was going to give Windows 7, or some other number?

---

### Post by dino99 on 2010-07-12
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by usersock on 2010-07-12
dino thanks for the quick reply. In your linked post, what does "go" mean? "*2) swap: about twice the real ram but max 2 go*"

I checked out PartedMagic as suggested in dino's link, but from what I saw, it simply used GParted to partition. The link also did not answer my original question; how much space should I put in the "free space preceding" box?

---

### Post by oldfred on 2010-07-12
Free space proceeding is if you want to put a specific partition in the middle or end adn leave the free space availble before that partition for another partition. If you plan ahead then working from left to right you have no free space in front.

You should make the windows first so it is a primary partition. All the other partitions can be primary or logical but if you ever want more partitions you either have to leave room or make sure the extended partition is last where you could then shrink the data partition and add another partition. 
I would install the 80 for windows, 2GB or RAM memory size for swap, 20GB for Ubuntu and the rest as your data. You may also want a separate /home but that is up to you.

---

