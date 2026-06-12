---
title: "Horrible Dual Boot Problem - Error 15 repeatedly"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by ramnarayan on 2006-06-13
Hi

I recently installed Ubuntu Breezy on a Gateway MX6121 Laptop. Originally loaded with Win XP.

right now I cannot access the computer to give exact details so am typing it from memory:

The partitioning for the windows section is as such 
C: 10 GB - Primary NTFS
D: 4 GB - Primary VFAT - The recovery section
F: 5 GB - Logical (I think) - Data section made so that it could be accessed from both Linux and Windows

Linux Section (all the partitions were logical)
Swap 1.5 GB
/boot 106 MB
/root 8.5 GB
/home 30 GB

***
Problem

The install etc of Ubuntu Breezy all goes well - it boots into Ubuntu normally, I reboot to check if everything is working and am able to log into Ubuntu again

at the Grub options it shows
apart from the normal Ubuntu options
in the others section the following
Win NT/XP
Win Xp Home

So I choose the last - Win XP home
it boots normally and I am able to use this section normally - no problems

then I reboot and
boom
I get Grub Loading. Please wait ......
Error 15

and just a blinking cursor

It happened before and I read up on the forum and googled and the solution seemed to be reinstall

then exactly the same thing has happened after reinstall

So what do I do: I don't have recovery disks for the in section since I was confident that Linux won't screw up (having done similar installs on atleast 4 other machines)

I can reinstall and try athe first of the Win boot options instead of the second 

Could the problem be that none of the linux partitions are Primary ????
***
but what advice and suggestion

(no I cannot upgrade to Dapper as I live in a remote place , dpon't have access to Dapper, and don't have the bandwidth)

will appreciate your urgent advice

thanks
ram

---

### Post by ramnarayan on 2006-06-13
Continuing from the previous post
I reinstalled Ubuntu Breezy - and it seems to be ok now (touch wood, cross fingers and everything else) but the first option that GRub shows (as part of other OS') is the recovery section and the second is the usable Win XP OS. SO after install I tried to go to the first section and it went into recovery mode and froze so was forced to poweroff. and then it seems to be ok so far.

SO AM WONDERING:
if the ubuntu install needs a poweroff before restarting ???
its never happened in other machines before , so why should it happen now.

thanks
ram

---

