---
title: "Ubuntu won't boot after video card upgrade"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by kahlil88 on 2008-01-27
I'm running "Gutsy Gibbon" (7.10) on a Dell Dimension 2350. When I tell the BIOS to use a PCI video card instead of the onboard video, Ubuntu won't boot, it just freezes with the loading bar at maybe 10%. What is the proper way to go about upgrading a video card? Is there some sort of "safe mode" that might detect the card and install the right driver from the CD?

---

### Post by jeffus_il on 2008-01-27
Soon after powering the machine up, after starting .. is printed on the screen, a menu will be displayed, normally the first entry is chosen automatically, use the down arrow once to choose the second entry "recovery mode"

After this at the command line reconfigure your X Server using ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ATIuser on 2008-03-09
I have the same issue on the same PC with an Nvidia GeForce Fx 5500 PCI expansion graphics card. I had the same issue with my old ATI Radeon card. So far, it seems to me to be an issue with the Dell proprietary motherboard.

The above command I can say for a fact wont work because I've tried to do that and it still gets stuck at the point where it tries to load the hardware drivers. Is there some kind of option that can be passed to the kernel to fix this issue?

---

### Post by Tuxtur on 2008-04-02
I just replied to the same question in another post, here is the link to that answer
[http://tinyurl.com/37xofe](http://tinyurl.com/37xofe)

---

