---
title: "Ubuntu on Vista"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by obscured47 on 2007-05-26
Hey guys,

I'm using an HP dv2000 laptop with Windows Vista installed for 3 weeks now and vista is driving me crazy soooo I decided to try ubuntu. I have 40gb free in my main partition (there's one 5gb partition for recovery). Does ubuntu cd have a partition manager to resize the partition of windows or do I have to do anything before I boot from the cd?


Cheers ;)

---

### Post by merlinus on 2007-05-26
Ubuntu live cd has a partitioner.  After it is up-and-running, click the Install icon.  You will have to answer a few questions, and then it will take you to the partitioning menu.

I recommend defragging your windows partition before starting.

Good luck!

-merlin

---

### Post by DJ Wings on 2007-05-26
Yes, defragging is always a good idea before partitioning, because it rearranges the drive space so it can be pinched off into other partitions. Otherwise, don't sweat it- and remember to back your data up. Just in case. ;) Welcome to Ubuntu!

---

### Post by obscured47 on 2007-05-26
Thanks for the instant replies :)

One more thing. I have to keep my Windows running for a few more weeks (so I need to have some space on the windows partition). I've got 40gb now. Ubuntu won't take all of them right? I was thinking of 25gb for Ubuntu. And I'm guessing it makes the swap etc on its own right?

By the way, will it be easy after some time to make the windows partition smaller and the other one bigger? Or will I have to reinstall?

Thanks again!:)

---

### Post by flip_flop on 2007-05-26
vista has shrink drive command in control panel\administrative tools\computer management.  Select disk management and then select the drive you wish to shrink, click on more actions and shrink.

Vista on some systems has a partition which is not viewable by any disk management tools for security.  If you  overwrite this area you will destroy your oem recovery tools and will not be able to restore vista back to factory standard settings.

I recomend you make a note of how much space is not accounted for on your hard drive ie. 100 gb hard drive but with only 95 gb of disk space.

---

### Post by obscured47 on 2007-05-26
hmmm no offense to our lovely windows (not :P) but should I trust that?

---

### Post by flip_flop on 2007-05-26
It worked on my laptop - with any problems except ubunto does its own thing with the partitioning in particular the swap file. It will decide how big it wants and where it puts it.  Vista booted fine first time after installing ubuntu

---

### Post by obscured47 on 2007-05-26
ok, defragmenting now ;)
thanks everyone!

---

### Post by obscured47 on 2007-05-27
ok i've done a defragment and I tried to shrink my windows partition from Administrative Tools but it won't work. It says I don't have enough space for it (!!! i do!). If I go straight to Ubuntu partitioner, will I be able to make choices? (eg. just 25gb of my space to windows and the rest left for windows)

---

### Post by flip_flop on 2007-05-27
I believe this down windows virtual memory using your hard drive try reducing your virtual memory

---

### Post by Pumalite on 2007-05-27
> **obscured47 said:**
> ok i've done a defragment and I tried to shrink my windows partition from Administrative Tools but it won't work. It says I don't have enough space for it (!!! i do!). If I go straight to Ubuntu partitioner, will I be able to make choices? (eg. just 25gb of my space to windows and the rest left for windows)

Forget about partitioning  unless you had a partition made before they installed Wimdblows. I had to fight with XP and at the end I TrueImaged Windblows and Packed in an external drive. Good luck!

---

### Post by merlinus on 2007-05-27
Try setting virtual paging in windows to zero, and then re-sizing the partition.  If this works, after installing ubuntu, change the paging size to something less than it was.

Also, follow flip_flop's advice about not inadvertenlty trashing some hidden partition for restoring windows that was created by the OEM.

Good luck!

-merlin

---

