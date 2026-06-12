---
title: "Partitioning"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by Saca_Saca on 2005-05-24
Hello,
What would be the ideal way to partition a 200gb drive for Ubuntu?
I will be using it for games and a few commercial apps.

I would also like to add the Ubuntu documentation/support is second to none.
I have learnt a great deal in the last two weeks, and i am greatful for all the hard work put into the Ubuntu community.
I have tried Linux in the past only to return to windows due to a lack of "good" support...there is no looking back now! ;-) 

Thanks, Darryl

---

### Post by JonahRowley on 2005-05-24
This depends on how much data you have and where you want to install the games to.  When in doubt, one giant partition works, but is not ideal.  Having a **/home** partition that will be persistent between installs and upgrades is very useful, even if you have to reinstall all your games.  You're going to have to guess how much space your games will take, add a few gigabytes for Ubuntu itself, and that would be the minimum you should use for your root partition.

---

### Post by cinematography on 2005-05-24
I have my computer partitioned like so: 

/ (10 gig)
/home (60gig)
/boot (50mb)
/swap (512mb)

It may not be the best solution but it's the one that works for me. :)

---

### Post by Saca_Saca on 2005-05-24
Would it be a good idea to have a partition for /usr/local for games. I will be installing a few big games (UT2004,Half Life,Doom3..etc)

---

