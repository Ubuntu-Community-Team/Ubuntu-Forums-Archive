---
title: "Transferring Ubuntu new PC"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by NJC on 2007-03-28
I want to transport my Ubuntu 6.06 drive over to a new PC. I was hoping to keep my current PC config (xorg.conf/menu.lst) as a backup. I've already booted the new PC (PIII/933Mhz) with LiveCD and it seems to recognize all hardware. 

I'd like to place an entry in menu.lst that will boot using both PC config files. Any suggestions for this transfer?

---

### Post by pradeepadapa on 2007-03-28
ubuntu automatically updates the menu.lst file according to the hardware on the present system .... so there will be no problem fr u abt the replacing of an entry in menu.lst file

---

### Post by NJC on 2007-03-29
I didn't get the new PIII/933Mhz (Optiplex G110) machine working because it needs 16 chip (unbuffered?) SDRAM that I don't have. But I did transfer the drive over to it last night. Here's what I had to do:

- disabled auto mounting of Win drive in fstab (not sure if this was necessary) since the new machine did not yet have a Win drive to mount.

- changed the path in grub boot to hda1 from hdb1.

Booting drive from old machine in new machine of course crashed X with the following error: "GDM couldn't start because X was not configed properly." Note that this kernel automatically makes xorg.conf backup so I ran

```
sudo dpkg-reconfigure xserver-xorg
```

and was able to configure the graphics card and start the machine. That was really the only problematic config since I was using the same monitor. All other hardware seemed to be recognized.

I had to switch the drive back to my main machine so I saved the contents of xorg.conf to file xorg.conf_DELL. So I have the configuration when I try again. I also place a line a "Dell" line in my menu.lst to properly point to hda1 just to save a few extra steps.

---

