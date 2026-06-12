---
title: "Windows 7 not booting after ubuntu install"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Notn4 on 2012-05-15
I hope I'm posting this under the correct category....


anyway, I'm running a system where my main OS is Win7

I have 2 HDDs, one is a 1TB drive which is used as system drive for Win7 + all data I have, the second HDD is 300GB and has been previously used for dualbooting XP but its not in use anymore and the XP on it has been erased long ago


Now I went and installed Ubuntu 12.04 on the second drive, formatting it on the same time... Ubuntu works great and I really like it so far but Win7 won't boot anymore, GRUB2 doesn't detect it at all, tried updating it too with no effect.


Windows 7 repair disc doesn't even recognize the Windows 7, that I managed to solve by running a few commands in Win Recovery console. Then after trying to fix boot via Win7 disc it still fails...


The error I get at boot is something similar to "No MBR found" 


I've gone through multiple threads that revolve around the problems caused after trying to dualboot, no luck.

The thread that helped the most has been this one [http://ubuntuforums.org/showthread.php?t=1310519](http://ubuntuforums.org/showthread.php?t=1310519) as post #7 shows some commands he used to get about 50% through his problem but it only made my windows repair detect my Win7 installation, and it also claimed that it had fixed the problem but it still failed to boot Win7


Please help, I really need to get that Win7 installation working again, its my main system and my main OS!



EDIT: managed to solve this by going on the ubuntu irc channel! great help with great speed! anyway the solution (such a wierd one) was to run those commands in the windows recovery console that I had tried before, just to it 3 times with restarts between and then perform a boot repair from the repair GUI on win7 disc... after that I managed to boot into win7 but not ubuntu without rearrannging the boot order of drives, so I put the ubuntu drive first in line and booted ubuntu, updated grub and that worked!

---

### Post by oldfred on 2012-05-15
Do not run any repairs until we review the Boot-info report. Post link it creates.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

### Post by shimana on 2012-05-25
Hey guys. 

I'm also new to ubuntu community and also new to linux. 

I've had the similar problem before and the problem was fixed by updating GRUB (I was using crunchbang linux by then tho). Now with the installation of the new LTS of ubuntu I have a different problem. Windows is shown in the GRUB but wont boot. I made some mistakes I guess by installing GRUB in different partitions but dont know the solutions to the problem. 

I've tried windows repair which couldnt find a start up problem so here is the report you asked from the started of this topic. Hope you can help.

[http://paste.ubuntu.com/1006140/](http://paste.ubuntu.com/1006140/)

Thanks in advance..

---

### Post by wilee-nilee on 2012-05-25
> **shimana said:**
> Hey guys. 

I'm also new to ubuntu community and also new to linux. 

I've had the similar problem before and the problem was fixed by updating GRUB (I was using crunchbang linux by then tho). Now with the installation of the new LTS of ubuntu I have a different problem. Windows is shown in the GRUB but wont boot. I made some mistakes I guess by installing GRUB in different partitions but dont know the solutions to the problem. 

I've tried windows repair which couldnt find a start up problem so here is the report you asked from the started of this topic. Hope you can help.

[http://paste.ubuntu.com/1006140/](http://paste.ubuntu.com/1006140/)

Thanks in advance..

Yes you put grub in the windows boot partition, you can use a ubuntu live cd to hopefully fix this with this link.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You would need to check if the grub notations are gone by running the boot info summary from the boot-repair again, if so just run the recommended repair on that tool, and you should be set.

If this tesdisk does not clear this repost in your own thread with the script again and let us know if you have a recovery or install disc for windows to repair with.

---

