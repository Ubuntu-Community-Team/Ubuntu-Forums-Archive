---
title: "screwed up dual-boot laptop"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by vizitorq on 2007-09-13
so i did my first ubuntu install on my laptop instead of my pc. this laptop already had windows xp installed and running perfectly. this was a laptop i got for christmas and it had all the HP stuff already installed on it, with a partitioned D- drive that was used as the hp system restore partition in case anything went wrong, you wouldn't need the CD itself to recover.

so i defrag my C-drive. then i boot with the liveCD and use GParted and allocate about 50 gigs of free space for ubuntu. then i run the install, everything works smoothly. it reboots, i take out the cd, and bam, upon startup i'm given an option to boot into linux or windows. so i boot into linux and it works, i play around with it for a while.

then, i restart the computer, at the option menu i choose to boot into windows this time. instead of booting into windows, it gives me this HP recovery program which takes about 30 minutes to go through. then, i'm given another program which basically asks me to setup my computer all over again (name, computer name, location, etc). and finally it boots into windows, and most of my programs are gone. but my partition is still entact the way it was when i used GParted. now it says my windows partition is 50 gigs, when before it was 100gigs.

so i restart, and it no longer gives me the option to boot into windows. i guess when it recovered windows it over-wrote the filesystem, but left the partition entact. not sure how common that is.

what am i supposed to get from all of this? i don't understand. is most of my data from my windows machine gone? should i run the live cd and open up my windows harddisk in a window manager and see if i can find the missing pictures and audio files? what could i have done wrong?

---

### Post by louieb on 2007-09-15
Sounds like the Ubuntu installer got confused and thought your recovery partition was your windows install. Then when you booted to what you thought was XP you got the XP recovery. From what I've read the recovery process put XP back the same as when the machine was new. 

Hindsight is 20/20 but if you had posted at that time. Someone could have helped you change the boot menu to load your XP install instead of the recovery program. 

May still be able to get some of your data back go to [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and see what it can do for you.

---

