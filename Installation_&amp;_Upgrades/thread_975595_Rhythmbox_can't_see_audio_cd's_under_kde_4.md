---
title: "Rhythmbox can't see audio cd's under kde 4"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Patriko_H on 2008-11-08
I just upgraded to Ubuntu 8.10. My system has the kde destop added since users like parts of both desktops. When using 8.04, Rhythmbox ran fine under kde. After upgrading to 8.10 rhythmbox recognizes an inserted cd under gnome but not the new kde4. What must I tweak so it can again see cds when they're inserted?

thx,
patrick

---

### Post by SuperSonic4 on 2008-11-08
I suspect it's something to do with the HAL [Hardware Abstraction Layer] daemon. What happens if you type ```
/etc/init.d/hal start
```

This is just a guess

---

### Post by Patriko_H on 2008-11-08
> **SuperSonic4 said:**
> I suspect it's something to do with the HAL [Hardware Abstraction Layer] daemon. What happens if you type ```
/etc/init.d/hal start
```

This is just a guess

Thx for the guess.  I tried (re)starting the HAL, it was already running, no effect on Rhythmbox seeing inserted CDs. 

Additional data:

1.Under under a Gnome session the CD is recognized and a window pops up asking me what I want to do with it. So it appears the device is being detected and handled properly at least under Gnome.

2.Under KDE 4, if I start up Sound Juicer it does see the CD and respond properly. 

3. Amarok doesn't see the cdrom drive either, I tried the auto device search, still no help.

4. I can't open the CD in the Dolphin file manager, can't figure out where in the FS it is. 

5. Can't mount /dev/cdrom manually. fstab had the entry ( possibly from earlier versions ) of /dev/hda /media/cdrom0 .... When I tried this I was told /dev/hda didn't exist. 

6. I've tried to track down how Sound Juicer is accessing the cdrom drive but haven't yet been successful.

Any more ideas?

---

### Post by tanzoniteblack on 2009-02-15
Audio CD's don't mount manually well, they run off a different file system type then data CD's and the like.  I had a similar problem with Amarok myself, though I haven't found the cure for Rhythmbox in KDE4 yet.  I presume you have multiple CD drives?  If so, if you figure out which /dev/cdrom number the drive you want to play CDs from, then you can go into Amarok's settings, configure, and then under the engine tab you can point Amarok to look at the device you actually want it to play audio CDs from.

---

