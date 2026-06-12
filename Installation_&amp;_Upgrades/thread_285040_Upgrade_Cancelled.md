---
title: "Upgrade Cancelled"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2006-10-26
Well, I "was" going to upgrade to 6.10, but after hearing a lot of people having issues with getting X to work after the absolute torture I had to go through to get it working in the first place, I decided to cancel my upgrade via synaptic and wait for a little while.  Not to mention that the servers are bogged down and I was only getting 70 kB/s, lol.  Anyway, after restarting the machine (only way I could find to kill the upgrade) it now says I have 450 updates, but I didn't actually "install" any updates, it was only downloading them.  Any suggestions on how to clean up the mess I made?

---

### Post by T.Louis on 2006-10-26
> **marcusdean.adams said:**
> Well, I "was" going to upgrade to 6.10, but after hearing a lot of people having issues with getting X to work after the absolute torture I had to go through to get it working in the first place, I decided to cancel my upgrade via synaptic and wait for a little while.  Not to mention that the servers are bogged down and I was only getting 70 kB/s, lol.  Anyway, after restarting the machine (only way I could find to kill the upgrade) it now says I have 450 updates, but I didn't actually "install" any updates, it was only downloading them.  Any suggestions on how to clean up the mess I made?

I had a painfull 15-20kB/s. I installed 6.10, and I had the issue with xserver not starting. I got lucky, and just installed the offical ATI drivers and it started. Only thing that is ugly is the splash screen but I hear thats because of the .17 kernel.

In any case I'm interested in hearing someone replying with how to get rid of the updates, cause at one point I wanted to delete around 300 myself when my net connection dropped during the DL. ;)

---

### Post by gerowen on 2006-10-26
Well just so happens I downloaded an .iso of the CD last night, and it was quicker for me to boot the CD, reconfigure xorg so I can get into the GUI and install Edgy than it has been for my wife's laptop to upgrade via synaptic, which started before I decided to just format and use the CD, and is still going now...and it appears as if some of the repos are down too, I can't connect to the one that has my nvidia-glx driver.

---

### Post by ooberallen on 2006-10-26
I was wondering if anyone has tried to update off the cdrom after canceling the update manager's download.  I'm tempted to try it since my download speeds are fluctuating between < 1k/s - 40k/s and I don't feel like sitting around waiting 10 hours for the download to finish especially since I was able to download the iso @ 300 k/s off a mirror.

---

### Post by gabrielsaldana on 2006-10-26
All you have to do is edit /etc/apt/sources.list replacing edgy back to dapper and you will no longer have all those updates listed.

I have one question though: how do you upgrade from the CD only? I inserted the disc and added it as a repository but does that mean that I will upgrade everything from there and not use the online repositories at all? That would come very useful to do while I'm offline traveling in my car.

---

### Post by ooberallen on 2006-10-26
from [https://help.ubuntu.com/community/EdgyUpgrades:](https://help.ubuntu.com/community/EdgyUpgrades:)

If you have the edgy alternate install CD, you can save bandwidth by using:

gksu "sh /cdrom/cdromupgrade" 

I figured the install cd was the iso I was downloading.

---

### Post by faeez on 2006-10-26
I'm about to cancel my update manager download, it still has 11 hours left and I should have the alternate iso in 10 minutes.
To upgrade from the cd simply use:
gksu "sh /cdrom/cdromupgrade" 
you need to use the alternate cd
check out [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by ooberallen on 2006-10-26
has anyone canceled the update manager download and updated from cd yet?

---

### Post by FakeOutdoorsman on 2006-10-26
Do you need the alternate CD to upgrade via CD?  I ran the following command and got errors with the standard Edgy install disc that I quickly downloaded with bittorrent:

gksu "sh /cdrom/cdromupgrade"

I'd supply the errors I received, but I don't have them with me now.  I'm guessing it didn't work because I used the standard install disc instead of the alternate install disc.

---

### Post by xJudahx on 2006-10-26
Yes, you need the alternate install disc.

I cancelled the upgrade and downloaded the alternate cd, then installed via cd, and it worked well.

---

### Post by ooberallen on 2006-10-26
I havent tried upgrading yet, where can i download this alternate cd? the iso I got was off the ubuntu download page off one of the mirrors.

---

### Post by PrinceArithon on 2006-10-26
Yeah upgrading right now sucks really bad.  I half way upgraded through the upgrade manager which took only a couple hours, but now I'M running the sudo apt-get upgrade whatever it is the command is.  Well no I'M not after reading this thread I stopped it.  IT sucks that it's running at 20 kbs.

Anyway I think I will wait...even though right now I seem to be getting an error from nautilus.....maybe if I restart it will be ok...I sure hope there are fixes by next week.  

I heard it was relatively painless upgrading from breezy to drake.  I think I'll just wait a week or 2 before I upgrade now.  By then no one else should be upgrading and there should be fixes to what is going on....

Aaron

---

