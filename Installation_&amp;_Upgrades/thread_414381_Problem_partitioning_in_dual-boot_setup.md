---
title: "Problem partitioning in dual-boot setup"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by adrenjarvi on 2007-04-19
Hello all. I am a complete linux nooblet, but I finally gave in to the flirty stare of ubuntu. I had a feisty fawn disc all burnt, a dual-boot setup ready to go. My windows XP PC has two harddrives- C:\\, a 100 gig drive that holds just documents, and then D:\\. a 160 gig that holds the windows system file. In the gnome partition manager, i set it so that my D:\\ drive would have 36 gigs left dedicated to it, then alot for the linux partition ( I plan on having fun :D) and then 1 gig for the linux swap. there was an error during the partition, so i attempted a similar plan on the other drive- resizing the partition to 88 gigs and dividing it up similarly. that also failed. My question now is twofold;

1. How do I dual boot this OS and partition it effectively, and 2:

2. My drives in windows are now only showing 88 for C and 36 for D. In the gnome partiton manager, it is showing them both as taking up the entire disk, with a precise half of their space taken up ( impossible). 

What can I do to fix this, and hopefully, my noobness?

Thank you!

---

### Post by mikesignguy on 2007-04-19
i think what you need is to move windows to one part of the disk
you can do it two ways

the first is harder to do and has always worked for me .. the second is easier but takes more time and has never worked for me


the first is to use gparted (i think fiesty might have it on the live cd ...not sure)
it is a program that is easy to use and you can burn it to a disk just like you did for fiesty
you can even parttion and format the HD

gparted.sourceforge.net/livecd.php

the second is to defrag windows and turn of it page memory , then run fiesty live cd and hope it sees the empty part .. ??????

---

