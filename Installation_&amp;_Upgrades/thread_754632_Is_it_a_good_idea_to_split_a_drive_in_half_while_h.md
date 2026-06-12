---
title: "Is it a good idea to split a drive in half while having Ubuntu on both?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by sgbrix on 2008-04-14
I’m ready for another rig with 3 ide’s and one sata drive. Will do the 
[http://www.bleedinedge.com/forum/showthread.php?t=22524]("http://www.bleedinedge.com/forum/showthread.php?t=22524") switch approach again. Since one do not have to worry about upgrades and boot messes.

The first two ide’s is for windows and the sata and the 3’rd ide is Ubuntu. My question is simply this. I always partitioned the primary C drive in windows 50/50 so that when that operating system eventually crashes which it always seem to do..., you can restore whatever there was on the second partition quickly. Is this something that also would be beneficial for an Ubuntu’s main drive? I’m having the sata drive as the main drive for Ubuntu. For a 200g drive 50/50 or how much?

Sg Brix

Ps,
For anyone that like to try this, what I did before is always have power on the two slave ide drives whatever operating system is being used. Alas before the switch. For it all to work tell your bios that these drives do not exist. Both windows and Ubuntu will find them anyway. This way it will not hang when you boot up Ubuntu. (Some Mboards chooses the ide drives before the sata drives and that could get you in trouble since there is no operating system on the slave drives).

---

### Post by hyperair on 2008-04-14
Well for Ubuntu the recommended is usually to put /home on a different partition. That way, if you ever need to install another Linux distro or reinstall Ubuntu, your settings are always intact. All your program settings will be exactly as you left them before reinstalling.

---

### Post by sgbrix on 2008-04-14
Thanks Hyperair, I figured as much,  but how much would you suggest to keep on the Ubuntu operating system side including for future programs etc? I see all different numbers mentioned here. 

SG Brix

---

### Post by hyperair on 2008-04-14
I'd actually leave 20GB aside for the operating system side, just to be safe. Under most circumstances you can allocate 10GB only, but I've installed GNOME, KDE and KDE4 on this computer. So... I've allocated 35GB for the OS, and used 12.5GB. But like I said, you could probably make do with 10GB. 

Either way it's not totally permanent as you can resize the partitions if you don't like your original configuration.

---

