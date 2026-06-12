---
title: "Ubuntu 9.10 take 5mins to load !!"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by Sydney2k on 2010-03-18
Installed Ubuntu 9.10 twice on a relatively new 1TB hard disk but still get the same slowwww boot problem. Harddisk was formatted with WinXP but when I installed Ubuntu 9.10 selected erase partition and installed Ubuntu 9.10 using the entire disk. Granted it is a old CPU - Opteron 165 with 1GB DDR1 ram in a Shuttle SN25P. But should it still take 5mins to boot !! 

I new relatively new to Ubuntu but I don't think that it should take that long to boot. 

Appreciate if the Ubuntu gurus could help. Thanks !!

---

### Post by phillw on 2010-03-18
Hi, and welcome to the forums.

The processor is about 4 - 5 years old. The people who really like boot times are mainly 'playing' with 10.04, but I'm sure one of them would look at your boot-chart if you post it for them.

The boot chart thread is over here --> [http://ubuntuforums.org/showthread.php?t=1343305](http://ubuntuforums.org/showthread.php?t=1343305)

Don't forget to be polite when asking, that is the 10.04 testing area & you're asking a favour ;-)  You can add that they were recommended as the best people to ask :-)  (Flattery always works)

If it is that ubuntu is asking too much of your processor, then you may want to have a look at xubuntu (runs xfce as the desktop) or lubuntu (runs lxde as the desktop) both of these are less processor intensive.

xubuntu is available in 9.10 now, lubuntu won't be fully released until 10.04 (End of April, when all the updates come out)

Both xubuntu & lubuntu (along with all the others) are in testing at the moment, if you'd like a 'sneak peek' at how they're getting along, grab the beta copies, due today / tomorrow, and pop them onto a partition (disk space, you have plenty of) and see how you get on with them

xubuntu is here --> [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
lubuntu is here --> [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

By the way, both those teams (and all the other teams) are looking for volunteers for testing.

Regards,

Phill.

---

### Post by Sydney2k on 2010-03-18
> **phillw said:**
> Hi, and welcome to the forums.

The processor is about 4 - 5 years old. The people who really like boot times are mainly 'playing' with 10.04, but I'm sure one of them would look at your boot-chart if you post it for them.

The boot chart thread is over here --> [http://ubuntuforums.org/showthread.php?t=1343305](http://ubuntuforums.org/showthread.php?t=1343305)

Don't forget to be polite when asking, that is the 10.04 testing area & you're asking a favour ;-)  You can add that they were recommended as the best people to ask :-)  (Flattery always works)

If it is that ubuntu is asking too much of your processor, then you may want to have a look at xubuntu (runs xfce as the desktop) or lubuntu (runs lxde as the desktop) both of these are less processor intensive.

xubuntu is available in 9.10 now, lubuntu won't be fully released until 10.04 (End of April, when all the updates come out)

Both xubuntu & lubuntu (along with all the others) are in testing at the moment, if you'd like a 'sneak peek' at how they're getting along, grab the beta copies, due today / tomorrow, and pop them onto a partition (disk space, you have plenty of) and see how you get on with them

xubuntu is here --> [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
lubuntu is here --> [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

By the way, both those teams (and all the other teams) are looking for volunteers for testing.

Regards,

Phill.


Thanks Phil... Perhaps I was asking too much of the Opteron 165 :sad:
Will give xubuntu a go when it comes out... Hope I have better luck with that. 

Thank again :D

---

### Post by tom4everitt on 2010-03-18
> **Sydney2k said:**
> Installed Ubuntu 9.10 twice on a relatively new 1TB hard disk but still get the same slowwww boot problem. Harddisk was formatted with WinXP but when I installed Ubuntu 9.10 selected erase partition and installed Ubuntu 9.10 using the entire disk. Granted it is a old CPU - Opteron 165 with 1GB DDR1 ram in a Shuttle SN25P. But should it still take 5mins to boot !! 

I new relatively new to Ubuntu but I don't think that it should take that long to boot. 

Appreciate if the Ubuntu gurus could help. Thanks !!

Maybe its because of the size of the root partition. You could try separate the system from the home folder this way:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

make the root (system) partition 20gb or so, and the rest for your home.

I really don't know if this could be the reason, but its never wrong to separate system and user files :) (You won't notice it when you use the system.)

---

