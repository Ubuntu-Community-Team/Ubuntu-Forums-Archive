---
title: "Partitioning Feisty dual boot"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Benchrest on 2007-04-30
I have set up dual boot before with 5.04 and 6.10. But in attempting to set up Feisty I am confused. I have seen some references to a new partitioner for Feisty that replaces gparted so maybe that is my confusion.

I have a desktop with a 40gb master drive "C" that is indows/xp. I have a second drive mounted as slave that is 80 gb. I have it partitioned in to two 40 gb drives "E" and "F". "E" has my XP page file and some back up data files. "F" is empty. I want to use "F" for Feisty. When I start the install from the live CD for 7.04 after time zone and language questions it ask me about partitions. It shows hda master of 40 gb that is my indows/xp. It also shows an two hdb's slave. one is hdb1 which I think is my page files and backup. It also shows a hdb5 which I think is where I want to put Feisty. I want to set up several partitions for root, swap and home, etc. in this 40 gb area. When I enter the first one it doesn't seem to want to let me define what its for and instead of letting me define them all and showing how it will look as gparted did, it wants to go ahead and create the first one before letting me enter the second one. and Its not very clear if that first one is root, swap or whatever. Perhaps I need direction to a guide on how to use this new partitioner but I have searched and not found one. Any guidance would be appreciated. I suspect what it is defining is the total space available to Feisty and after this page it will ask how to sub divide it. But that is not very clear and I don't want to destroy my page file.

---

### Post by bulldog on 2007-04-30
Yes.well use the GParted live cd [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Make your partitions as you would have them and apply the changes.
When done exit the gparted live cd.

Boot up the ubuntu install cd and when you come to the partitioner choose manual partition.
Mount your previous created partitions as you like,set them to format again,set the bootfag on the right partition and apply.
Continue the install.

---

### Post by Benchrest on 2007-04-30
Thanks I'm up and running.

---

