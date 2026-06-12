---
title: "no option to partition?? HELP PLEASE!!"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Kaneda187 on 2008-06-26
doing a fresh install of Hardy, evertings goin good, and then it comes to the partitioning and it starts it up but wont give me the option to allocate space to my other os??
 ( like set it 50% windows 50% Ubuntu ) 

im really mad and want it to work help quick please!!

do i have to change some settings on my hdd in windows??

---

### Post by Midwest-Linux on 2008-06-26
If your other OS is Vista, use the built in Vista shrink partitioner. It works great and it only takes a few minutes. Then after you have freed space. Reboot and then Install Ubuntu on the freed space when you get to the partitioner.

 I can't help you beyond this as I have no idea what your other Windows you are using ...Vista, XP, 2000. 


I recommend using the alternate install CD for Ubuntu. Thats my recommendation, as I use the alternate version for all my Ubuntu or Xubuntu installs. But you don't have to, there is no requirement but I can see exactly whats going on when installing.

---

### Post by Kaneda187 on 2008-06-26
it be xp:) ive done this all b4 and it worked great but i kinda messed it up by tweaking it a bit much so i wanted to do a fresh install its really annoying sice it woked last time:confused:

---

### Post by Midwest-Linux on 2008-06-26
> **Kaneda187 said:**
> it be xp:) ive done this all b4 and it worked great but i kinda messed it up by tweaking it a bit much so i wanted to do a fresh install its really annoying sice it woked last time:confused:

 Would it not be easier to undo your "tweaks" and avoid a reinstall? There should be a way of just trying to do a reinstall via a command line in the terminal. 

 You may not really have much space to do a partition since you already have Ubuntu on there and another OS and if both OS's are pretty much filled with files. Then problem could be is that the hard drive is full. Which means if thats the case, you might have to move or delete some files to free up some hard drive space...though I am only speculating here...but that could be the cause of refusing to partition. 

 Also you reinstall Ubuntu and end up with another partition, you then could have two Ubuntu partitions. Another thing to consider is to use the alternate install CD and use the CD to REPAIR the installation.

---

### Post by Kaneda187 on 2008-06-26
> **Midwest-Linux said:**
> Would it not be easier to undo your "tweaks" and avoid a reinstall? There should be a way of just trying to do a reinstall via a command line in the terminal. 

 You may not really have much space to do a partition since you already have Ubuntu on there and another OS and if both OS's are pretty much filled with files. Then problem could be is that the hard drive is full. Which means if thats the case, you might have to move or delete some files to free up some hard drive space...though I am only speculating here...but that could be the cause of refusing to partition. 

 Also you reinstall Ubuntu and end up with another partition, you then could have two Ubuntu partitions. Another thing to consider is to use the alternate install CD and use the CD to REPAIR the installation.
Am nope that aint the problem cuz i did a total clean install windows first then ubuntu this is my second time doing it and i did everything the same! thanks by the way i appriceate the help!!:) ther must be some setting in xp cuz its like the ubuntu install isnt seeing the xp install and just wants to use the entire disk!:(

---

### Post by Kaneda187 on 2008-06-26
bump! please guys someone gotta have an idea??:confused:

---

### Post by lswest on 2008-06-26
manually partition it?  That should be an option.  Just resize the XP partition, make a partition (ext3) with mountpoint / and a partition of swap (1-1.5x your RAM), no mountpoint necessary.  If you want you can create a seperate partition for /home (that would then be the mountpoint) formatted as ext3 to save your settings if you ever do a fresh install of Ubuntu.

---

### Post by Kaneda187 on 2008-06-28
I actually just want to know why the ubuntu install doesn't see my xp install??

---

