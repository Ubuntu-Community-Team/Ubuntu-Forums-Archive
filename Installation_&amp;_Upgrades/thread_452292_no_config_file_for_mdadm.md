---
title: "no config file for mdadm"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by lls_draco on 2007-05-23
Hi,

[FONT="Arial"]I was doing an upgrade from 6.10 to 7.04 and during this process a pop up window about the mdadm system and  ask me whether to configure or to cancel and, by a stupid mistake :(, I canceled.
[/FONT]
As result a got no config file for mdadm system.

Does anyone knows how to solve this problem?

BWT, did I lost my data?

Thanks in advanced.

Cheers.

---

### Post by lls_draco on 2007-05-23
Some info:

I was able to find out the fstab file after and before the upgrade: file named 'fstab.txt' is after and 'fstab.pre-uuid.txt' is before.

I'm somehow worried about if would be able to save the data stored in  my home dir. I realised that it is still there. 

I really would appreciate some help.

Thanks in advance.

---

### Post by Soybean on 2007-05-23
Yeah, that mdadm seems to be causing problems for a lot of people during 6.10->7.04 updates. I was lucky, because when the window popped up for me, I got suspicious and hit Google before doing anything with it.

Now, I'm not really clear on what state your system is in. Can you boot at all? You've got access to your fstab, so that kind of sounds like you can boot... does this work? ```
sudo dpkg-reconfigure mdadm
```

I don't remember the exact details of what I did, but I believe it involved typing "none" into a box in the mdadm config screen. Also, my fstab looks more like your second one -- familiar devices instead of weird uuids. 

Anyway, I'd suggest searching around a bit for similar posts... I remember finding ones by a few different people whose systems got broken to different degrees by mdadm, but I don't remember the details.

---

### Post by lls_draco on 2007-05-23
> 
Now, I'm not really clear on what state your system is in. Can you boot at all? You've got access to your fstab, so that kind of sounds like you can boot... does this work?


The state is the following: When I boot the system start normally upto a point where mdadm complains saiyng

```

Loading. please wait ...
mdadm: No devices listed in conf file were found
             check root = bootarg cat /proc/cmdline
             or missing modules, device : cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/e7374f4c-9669-44f0-9d5c-8a82e3d9d24f does not exist. Dropping to shell!

modprobe: FATAL: Module raid456 not found

BusyBox 1.1.3 (Debian 1:1.1.3-3ubuntu3) Buit in shell (ash)

(initramfs)

```

And after that I tryied to do your suggestion in this shell but unfortunately I can not find this 'dpkg' progam,  I think it is not loaded.

Thanks anyway.

Cheers.

---

### Post by Soybean on 2007-05-23
Ok, well... first of all, I should answer your initial question: your data should be safe. :) You should be able to rescue it by booting from a Live CD and copying your data off, to a USB drive, or a network share, or whatever.

As for actually fixing the problem, the easiest way would be to back up your data and then format and reinstall from scratch. 

The more difficult way, if you don't want to have to start from scratch, is to try something like what pilpi did in this thread: [http://ubuntuforums.org/showthread.php?t=429609&highlight=mdadm+feisty](http://ubuntuforums.org/showthread.php?t=429609&highlight=mdadm+feisty)
His problem was similar to yours, and he managed to get rid of mdadm, although he then ran into another problem and ended up reinstalling anyway. So... that's not super encouraging, but it still might be worth a shot.

---

### Post by lls_draco on 2007-05-24
:) Thanks  Soybean !

I try the 1st approach, because it seemed me the most strait forward and easy. I backed up the data and install from scratch.

I think it is working perfectly.

Once more, Thank you very much.

Cheers,
L.

---

