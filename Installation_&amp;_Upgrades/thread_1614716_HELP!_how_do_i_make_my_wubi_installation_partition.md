---
title: "HELP! how do i make my wubi installation partition bigger?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by pinnacle65 on 2010-11-06
I installed Ubuntu using wubi, But I didnt assign much space, probably  like 17 gigs or something. My geting a pop up everytime my ubuntu starts  up saying i got low disk space, very low disk space, Im runing ubuntu  10.10. How do I add more disk space? How do i make the partition bigger.

---

### Post by wilee-nilee on 2010-11-06
Wait for qualified help here wubi is not used by a lot of users so the response may be slower, but here is a link to ponder while waiting.
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by bcbc on 2010-11-06
There are a couple of options.
1) move data off the virtual disk to the windows partition(under /host). This is the easiest and should work since a lot of the 17GB is likely multimedia files. If it's not maybe you have a problem since 17GB is a lot of data. You can run the disk usage analyzer - enter "gksudo baobab" - from command line to see where the space is being taken (stop it the first time it runs, and go to preferences and deselect the windows host or it will take forever). This will show what's taking all the space.

2) You can create a new virtual disk for /home. The wubi guide has a script - I can't vouch for this but I haven't heard of problems with it. 

3) There is a utility for resizing the root.disk - in fact it just creates a new root.disk (it's part of lvpm). I don't recommend this as lvpm is out of date and there are some complications. I'm working on a updated script to do this, but... I'm not sure it's a good idea anyway. Basically, say you wanted to go to 30GB, you'd need to create a new file of 30GB, copy the 17GB to it. Only after it's booted ok can you free up that 17GB.

4) Personally, I'd just create a 30GB partition or more, and just migrate the wubi install to it: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by pinnacle65 on 2010-11-06
> **bcbc said:**
> There are a couple of options.
1) move data off the virtual disk to the windows partition(under /host). This is the easiest and should work since a lot of the 17GB is likely multimedia files. If it's not maybe you have a problem since 17GB is a lot of data. You can run the disk usage analyzer - enter "gksudo baobab" - from command line to see where the space is being taken (stop it the first time it runs, and go to preferences and deselect the windows host or it will take forever). This will show what's taking all the space.

2) You can create a new virtual disk for /home. The wubi guide has a script - I can't vouch for this but I haven't heard of problems with it. 

3) There is a utility for resizing the root.disk - in fact it just creates a new root.disk (it's part of lvpm). I don't recommend this as lvpm is out of date and there are some complications. I'm working on a updated script to do this, but... I'm not sure it's a good idea anyway. Basically, say you wanted to go to 30GB, you'd need to create a new file of 30GB, copy the 17GB to it. Only after it's booted ok can you free up that 17GB.

4) Personally, I'd just create a 30GB partition or more, and just migrate the wubi install to it: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

well i threw 30gb as an example , but I actually want to give ubuntu much more, After installing ubuntu , now i want to keep it as my main OS so I want more space. I got a 320HD I want at least half of that drive for Ubuntu

---

### Post by wilee-nilee on 2010-11-06
> **pinnacle65 said:**
> well i threw 30gb as an example , but I actually want to give ubuntu much more, After installing ubuntu , now i want to keep it as my main OS so I want more space. I got a 320HD I want at least half of that drive for Ubuntu

That was the help I meant. You might consider as suggested looking at the option of transferring your setup to a regular install. Really due to the size you want it is probably best.

---

### Post by P4man on 2010-11-06
> **wilee-nilee said:**
> That was the help I meant. You might consider as suggested looking at the option of transferring your setup to a regular install. Really due to the size you want it is probably best.

+100
There is absolutely no reason to use wubi if you intend to use ubuntu as your primary OS (and every reason not to use wubi, one of which you just discovered)

---

### Post by oldfred on 2010-11-06
One more on conversion.

Even the designer of wubi thinks you should convert:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

