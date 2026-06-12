---
title: "X fails to start after 6.10 upgrade"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by mdavidn on 2006-10-30
I just upgraded my Ubuntu desktop from 6.06 LTS to 6.10 via the "official" upgrade method as specified on both the Ubuntu web site and this forum. Upon reboot, everything seemed to be working correctly until I received an ugly error informing me that X had failed to start. It is apparently missing a graphics driver.

I was previously using the "nvidia" driver from the non-free repositories for my GeForce 6200. However, I have tried modifying the X configuration to use "nv" and "vesa", but neither of those will load either. The exact X error for all three is as follows:

[INDENT][FONT="Courier New"](==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "vesa" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found[/FONT][/INDENT]

I don't know how to fix this. ](*,) Please help!

---

### Post by BLTicklemonster on 2006-10-30
How did you try using nv or vesa? Did you edit X11/xorg.conf or did you dpkg-reconfigure xserver-xorg? I found that just editing is simpler and works. But then you may not be able to do that... Have you been trying this from the recovery console?

See if you can edit sources, and add this at the end

```
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
```

then save, and then type

```
sudo apt-get install nvidia-glx
sudo apt-get upgrade

```
then

```
sudo nvidia-xconfig
```

then restart.

---

### Post by mdavidn on 2006-10-30
I'm just switching to the first console (Ctrl+Alt+F1) and using vim. Not sure if that's the "recovery console," but its the only console I know about when X isn't working. :)

Your directions produced slightly different output. Instead of X complaining that it couldn't load the "nvidia" module, the nvidia module was complaining about not being able to load the kernel module. I noticed that the update switched me to the 2.6.17-10-386 kernel. My previous kernel was 2.6.15-27-686, a different architecture. Not sure if that makes a difference.

At this point, I'd be content to get the vesa or nv drivers working. I remember the nvidia driver gave me some similar troulbe in the past, but I could always switch back to nv and X would boot.

---

### Post by mdavidn on 2006-10-30
I fixed the vesa and nv drivers by reinstalling ubuntu-desktop. The upgrade process had removed the old drivers without completing its upgrade of xorg or ubuntu-desktop.

I still can't get the nvidia driver to work, but I had this same exact problem in 6.06. The important thing is that X now starts. :D

---

### Post by sciurus on 2006-10-30
I had a smiliar problem. After upgrading, X wouldn't star because it claimed the driver and server version didn't match. I had to install xserver-xorg-video-all, which replaced the incompatible drivers from xserver-xorg-driver-all

---

### Post by mdavidn on 2006-10-30
I got the nvidia driver to work perfectly after switching my kernel to 2.6.17-10-generic. The nvidia kernel module does *not* seem to work with 2.6.17-10-386, which was the default kernel on this AMD Athlon XP machine.

---

### Post by Omnios on 2006-10-30
I had a problem with X and xserver failure. From the errors I noticed it was trying to point to the onboard video chip or wrong pci address. This was fixed by running 
```

sudo dpkg-reconfigure xserver-xorg

```


 It automaticcly detected to the right pci address

---

