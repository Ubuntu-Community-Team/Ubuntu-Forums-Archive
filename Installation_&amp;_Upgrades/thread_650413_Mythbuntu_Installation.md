---
title: "Mythbuntu Installation"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by bkr1_2k on 2007-12-26
Checking through the archives didn't provide any answers to my question, so I'll make it my first post here.  

I'm trying to install mythbuntu on a 933 P3 with 512 MB RAM and an 80G WD hard drive.  I have an ATI Rage 128 TV tuner card and a hauppage PVR 150.  On board video and audio are enabled right now via the bios.  

My problem is that when I get to the hard drive partitioning section of the install, I get a blank screen.  I don't get the "guided or manual" partitioning screen, just an empty window.  The bios recognizes the hard drive, so I'm assuming ubuntu should as well.  I'm using the mythbuntu 7.1 i386 iso, which I downloaded from the mythbuntu site.  The only thing I can figure is that either my iso is corrupted or the installer is broken somehow, but I'm willing to entertain the idea that I missed something.  

Any suggestions on how to partition this drive another way and skip this section of the install?

---

### Post by tech9 on 2007-12-26
> **bkr1_2k said:**
> Checking through the archives didn't provide any answers to my question, so I'll make it my first post here.  

I'm trying to install mythbuntu on a 933 P3 with 512 MB RAM and an 80G WD hard drive.  I have an ATI Rage 128 TV tuner card and a hauppage PVR 150.  On board video and audio are enabled right now via the bios.  

My problem is that when I get to the hard drive partitioning section of the install, I get a blank screen.  I don't get the "guided or manual" partitioning screen, just an empty window.  The bios recognizes the hard drive, so I'm assuming ubuntu should as well.  I'm using the mythbuntu 7.1 i386 iso, which I downloaded from the mythbuntu site.  The only thing I can figure is that either my iso is corrupted or the installer is broken somehow, but I'm willing to entertain the idea that I missed something.  

Any suggestions on how to partition this drive another way and skip this section of the install?

you could try to partition the drive with gparted.

```
sudo apt-get install gparted
```

from liveCD

let me know how that works out for you

---

