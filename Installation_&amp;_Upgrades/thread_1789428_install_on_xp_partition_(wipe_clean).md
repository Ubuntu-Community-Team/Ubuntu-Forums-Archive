---
title: "install on xp partition (wipe clean)"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by ppqq on 2011-06-23
Hi, I've used ubuntu for a week now and it looks like I can safely separate *for ever* with WinXP!  My Linux system is on a small [too small because I was not sure about how much to give it] extended partition on my win E:/ and sooner or later I would like to reinstall it on my larger logical partition, which has WinXP, C:/ (or sda1).

I've made a system backup ISO with Remastersys (LiveCD).  What is the way forward?  
1. Use my Live CD to format sda1 and install (then wipe off the first linux partition)?  
Will the system like having two Linux installs??

2. can I do it from inside Ubuntu by any means?

What's the typical method?  perhaps there's already some good threads on it, if someone could point me in the direction....sorry!! 
ideas please!

---

### Post by mörgæs on 2011-06-23
If you boot a live Ubuntu, you can run Gparted and delete the Windows partition(s).
After that you expand the existing Ubuntu to use the newly freed space.
As always, a backup is good to have.

Welcome to the free world!

---

### Post by ppqq on 2011-06-23
ok, i have gparted too.  i kind of thought that my old win partition was 'far' away on the hdd from my linux area, so joining the linux part with that formatted area would be messy!  tell me its not.

i have wine installed for just one prog (installed on ubuntu), will it be interupted with win wiped off?

---

### Post by mörgæs on 2011-06-23
People from a Windows background tend to be very concerned about fragmentation, but in Linux there is no need to worry. If you just remember not to load a hard drive more than 4/5, then Linux will take care that files do not get too fragmented. 

Wine is an application running inside Ubuntu. It does not communicate with Windows itself, and Windows can not see programs installed under Wine. They are completely independent.

---

### Post by ppqq on 2011-06-23
cheers for the help, i will try in the morning...

---

### Post by ppqq on 2011-06-24
Gparted worked a dream!  I used live cd to boot up, erase my win partition, move my sda1 over with resize, then move over my sda4 extended which contains sda5 and sda6 linux and swap, then move over and resize sda5.  the warnings told me that i might loose my boot record on sda5, but I've booted perfectly afterward.

---

### Post by mörgæs on 2011-06-25
Good, please mark the thread 'solved'.

---

