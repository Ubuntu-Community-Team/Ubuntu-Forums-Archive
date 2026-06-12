---
title: "Partitioning takes forever?!"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by blashphemy on 2006-08-21
Hi, I'm a new Ubuntu user. I got a new iMac so I'm trying to install Ubuntu alongside Windows on my old HP. I managed to boot from the CD OK, so I decided to run the installation. Everythings fine until step 5, where I decide to make the partition about 30 GB (pretty much the free space I had in Windows) and I click next. I got a busy cursor without any change it the screen and since nothing was happening in a while, I decided to let it run overnight, but this morning ABSOLUTELY NOTHING had changed. The program hasnt crashed or anything because I can press the cancel button and it will tell me "Installation will be aborted. Are you sure you want to quit?" or something like that. I can also run various other programs in the background. 

I wanna get Ubuntu installed but it wont partition? Please help....

---

### Post by unisol on 2006-08-21
you have a new mac an intel mac or an older mac

---

### Post by copycat on 2006-08-21
You should try "start ubuntu in safe graphics mode"... 

suc6

---

### Post by akshaysrinivasan on 2006-08-21
Well i experienced the same problem,only gparted wouldn't even start.I Would 
recommend you to  create some free space in the place where you want to install dapper first using gparted and then choose the "use the largest continuous free space option".this did not hang for me.hope this helps

---

### Post by Gun_Smoke on 2006-08-21
> **akshaysrinivasan said:**
> Well i experienced the same problem,only gparted wouldn't even start.I Would 
recommend you to  create some free space in the place where you want to install dapper first using gparted and then choose the "use the largest continuous free space option".this did not hang for me.hope this helps

I can't gparted to fire up either.. Have posted the issue [http://ubuntuforums.org/showthread.php?t=240816]("http://ubuntuforums.org/showthread.php?t=240816")

---

### Post by akshaysrinivasan on 2006-08-21
Then you can download the Gparted x86 bootable live cd and do the partitioning

---

### Post by avtolle on 2006-08-21
blasphemy: did you defrag your HDD first? Even though it looks like there is 30 mb free space, chances are, if you haven't defragged, you don't have 30mb contiguous free space on the drive. So, if you haven't, defrag; then defrag again; and, defrag again. If you have defragged, but only once, I suggest you do it again, as it is amazing how ineffective the native defrag utility is in Windows.  Once you are done with the defragging, then try to install. HTH.

---

### Post by blashphemy on 2006-08-22
alright, defragging helped, thx a lot :)

the weird thing is that I use Executive Diskkeeper, which is supposed to keep it automatically defragmented, but I guess not; it worked when I manually told it to defragment it though. Huh.....

---

