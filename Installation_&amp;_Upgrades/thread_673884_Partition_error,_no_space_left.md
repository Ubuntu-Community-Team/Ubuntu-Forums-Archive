---
title: "Partition error, no space left"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by spinoza666 on 2008-01-21
Hey,

I'm quite new to linux and need help with a little problem.

When I installed ubuntu 7.10 i spent 2 gb for swap and about 8 for /. Im unsure if i specified anything for /home, and that might very well be why Im having this problem.

About 10 gb have been allocated to the home directory so Im about to run out of space. The total is 100 gb, so I basically need to allocate remaining missing memory to my /home.

How do I do this?

---

### Post by c0met on 2008-01-21
I the installation is relatively new - which would mean you don't have lots of programs installed, I'd actually reinstall Ubuntu. 

Rather than use the partitioning program that's part of the install process though, I'd use the Partition Editor (GParted) that comes on the Live CD. To this, you,
[LIST]
[*]boot from the Live CD
[*]under System >> Administration you'll find the partition editor
[*]start this up and you will see the partitions
[/LIST]
If you have 100 gigs to use, I'd go...
[LIST]
[*]25 gigs for /
[*]2 gigs for /swap
[*]the rest to /home
[*]I suggest you use ext3 format
[/LIST]
Then when you run install and you get to the part that asks you to select a partitioning process, you choose "Manual". Double check the partitions that you have. Make sure that they are mounted /, /home, swap. You will also need to check "format" for /. 

Hope that helps.

---

### Post by Partyboi2 on 2008-01-21
You can boot into the ubuntu live cd and open up the partition editor (System>Admin>Partition Editor) and use the resize tool to increase the size of the /home partition if you have one or the /root partition if you don't.

---

