---
title: "Dual-boot delete to a clean install"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by BeingLostMayVary on 2010-01-11
The title may not be that self-explanatory, but I'll try that here. Currently I am running a dual-boot of kubuntu/xp. I want to switch over to Ubuntu entirely. How would I go about deleting or removing both of these operating systems to install a fresh Ubuntu on a nice spacey hard drive. If you could help me it would be appreciated. I already have Ubuntu Karmic on a Live CD to install it. I just need to figure out this mess.

---

### Post by raymondh on 2010-01-12
> **BeingLostMayVary said:**
> The title may not be that self-explanatory, but I'll try that here. Currently I am running a dual-boot of kubuntu/xp. I want to switch over to Ubuntu entirely. How would I go about deleting or removing both of these operating systems to install a fresh Ubuntu on a nice spacey hard drive. If you could help me it would be appreciated. I already have Ubuntu Karmic on a Live CD to install it. I just need to figure out this mess.

My suggestion

1.  back-up any files you might want to transfer to Ubuntu
2.  Boot into your ubuntu liveCD.  Proceed to install and in step 4, select 'USE ENTIRE DISK'.

Afterwards, you may wish to separate your /home from root (/).  That way, should you need to re-install for any reason, you just re-install over root whilst retaining your /home (and its' settings, files, etc).

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you wish to know more about partitioning and manual installations, some reference reads for you.

[http://ubuntuforums.org/showpost.php?p=1646977&postcount=1](http://ubuntuforums.org/showpost.php?p=1646977&postcount=1)
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

This may be for an OLD release but the 'basics' are still the same.

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/partitioning.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/partitioning.html)

Post back if you need assistance in creating partitions beforehand and manual installations.  Otherwise, have fun and happy ubuntu-ing :)

Raymond

---

### Post by BeingLostMayVary on 2010-01-12
OK thanks :) 
 
I'll post back when I've got it all done or have problems.

---

### Post by BeingLostMayVary on 2010-01-13
Ok I got it all up and working. It works great :)  Thanks for all the help. I'll try to do that thing you suggested this weekend for the /home.

---

### Post by Forbees on 2010-01-13
man raymondh you went overboard on the info needed lol

but i guess it could have saved time if problems happend :-p

---

### Post by raymondh on 2010-01-13
> **BeingLostMayVary said:**
> Ok I got it all up and working. It works great :)  Thanks for all the help. I'll try to do that thing you suggested this weekend for the /home.

Am glad as well.  Congratulations.  happy ubuntu-ing :)

Raymond

---

### Post by raymondh on 2010-01-13
> **Forbees said:**
> man raymondh you went overboard on the info needed lol

but i guess it could have saved time if problems happend :-p

LOL :)

Raymond

---

