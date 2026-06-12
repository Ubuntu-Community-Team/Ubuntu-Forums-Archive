---
title: "Installing Ubuntu for NAS"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by gianluca4 on 2014-06-07
Hello,
I’m in the process of building a NAS box, which should serve as a file server, plus some light server applications (mostly streaming). I have evaluated a few options and I would like to share my conclusions and ask a few questions before committing to it and throw away time (and potentially data). I would appreciate your comments and suggestions if you are interested in reading further.
 
**Relevant Hardware:**
[LIST]
[*]GA-E350N WIN8 (mini ITX, bit weak CPU, but quite cheap and with 4 sata ports. It should be fit for purpose)
[*]2 x 3TB WD Red (I’m considering possible expansion in the future)
[*]8GB DDR3 RAM
[/LIST]
 
**Considerations:**
[LIST]
[*]I think that the three most popular options for a project like this are:
[LIST]
[*]A dedicated NAS solution (FreeNAS, NAS4Free, etc.)
[*]Some form of Linux Server distro (Ubuntu Server)
[*]Some form of Linux Desktop (Ubuntu)
[/LIST]
[/LIST]
 
After having done some reading and weighing the possibilities, I have decided for Ubuntu Desktop because:
[LIST]
[*]NAS solutions seem to be quite complex to implement, maintain and to add functionalities on. Furthermore the various NAS forums managed to scare me away from ZFS: Pretty much every other post says “If you [add any small mistake or misunderstanding of procedures here], you will lose the whole pool, your computer won’t talk to you anymore and probably you’ll split up with your wife” (ok, I might have exaggerated a bit, but you get my point).
[*]Ubuntu Server is probably the best solution, but I’m not fully conversant with the CLI and to be honest I quite like the idea that if my main desktop dies on me, I can use this box as a provisional machine to do basic stuff.
[/LIST]

**Disks configuration:** I will go for Raid 1 (plus backups of course).
 
**Questions:**
[LIST]
[*]Installation. I suppose that there are mainly three ways to install this system
[LIST]
[*]Dedicate one extra disk as system disk. This obviously works, but it steals one precious SATA port
[*]Install the system on a USB stick. It should work, but there might be performance issues (the board only supports USB 2.0).
[LIST]
[*]Is there a way to push Ubuntu to have a priority in being retained in the RAM? This could help performance. Dedicated NAS system typically do this, but I have no idea of how to do it in Linux
[/LIST]

[*]Install the system in one of the data disks (it would therefore be mirrored to the other disk). I would be inclined to implement this solution, but:
[LIST]
[*]Is there a tutorial to achieve this?
[*]What should I do if I decide to expand the storage? I suspect that my only option is to add two disks and create a further mirror with them.
[*]I would lose some space, because I will be mirroring the system too, but that’s not a problem and actually might come in handy if there’s a system failure.
[/LIST]
[/LIST]
[/LIST]


[LIST]
[*]If my system disk or one of the data disks fails and I can’t/don’t want to rebuild the system, can I just stick the other data disk in a USB casing, connect it to a Linux box and copy the files from there assuming I haven’t encrypted the disk?
[/LIST]
 
I’m sure this is more than enough. Thanks a lot for making it through here.
 
Regards,
Gianluca.

---

### Post by tgalati4 on 2014-06-08
With freenas and nas4free you can boot off of a USB stick (2.0 is fine) and everything runs in RAM.  Configuration is saved on the USB stick so you can safely reboot the system and keep all of your settings.  That frees up your SATA port and you should be fine with 8 GB of RAM.  You can set up Ubuntu to run the same way, but it is not as convenient and you will have to research the best way to do it.

You could create some small, dedicated partitions across your TB drives and install the system to this small, mirrored RAID and be separate from your DATA RAID, but this is overkill for a home server and creates a boot problem if one of your disks has a problem.

I have been running nas4free for several years on an old Pentium I, 188 Mhz, 256MB RAM with several TB of data using a PCI SATA card.  It boots off of an old IDE drive, but I have mirrored it to a USB stick so I can boot off of it as a backup in case the drive fails.

The only way to offer real advice is for you to pick a direction and start installing and configuring and take notes on what works and what doesn't.

---

### Post by gianluca4 on 2014-06-09
Thanks for your reply tgalati,
as I said I would rather have a "full" Linux system running. After some more digging and to keep things simple I am currently thinking of installing the system on an old laptop hard drive, although that costs me one SATA port. 
My only question/concern now is: If that drive fails (or if one of the RAID 1 data drives fails) can I connect one of the good data drives to another linux box via USB and simply copy the data from there, or even a "simple" RAID 1 configuration will make it difficult to recover the data in this way?

Thanks,
Gianluca.

---

### Post by Dale_Whitnall on 2014-06-09
Assuming that you use madam to implement your raid, you should be able to read the data from it on another system if the raid data stays intact.  I have moved a raid 5 setup between servers before without losing anything.  I also recommend using an stand alone drive for the system disk, if you can spare the sata port.  You did mention that you were going to use this for streaming, I too had the raid setup for this purpose, though lately I moved away from that setup as it was a pain to keep running in my case.  I ended up moving to SnapRAID, and mhddfs to pool the drives together.  Works perfectly for my media streaming storage.
Another thing I learned from my system disk crashing is to keep another copy of your config files on another drive, it makes it a hell of a lot easier if it ever happens.

---

