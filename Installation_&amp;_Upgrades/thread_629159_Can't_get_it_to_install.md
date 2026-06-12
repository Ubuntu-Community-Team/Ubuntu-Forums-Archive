---
title: "Can't get it to install?"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Just4 on 2007-12-02
Alright, my system hangs anytime I try to install, heres what happens, I have a Live CD that I requested, which is 32-bit v7.04, and I got the newest version 64-bit alt install

Anytime I load the livecd as soon as it gets to mouse cursor, system hangs, I've left it like that for an hour trying to see if it would boot, but it does not, I've tried noapic nolapic and apic=off as boot command lines, only way I can actually get to the desktop is if I use acpi=off, but then my USB mouse doesn't work.

I can get the 64 bit version to install, but it hangs on the desktop as well

The specs for this system is a Athlon 64 Socket 754 at 2.0Ghz, 1GB RAM, SATA Hard drives, GeForce 6600 PCI-E 128MB card, is there anyway I can get ubuntu on here? I can boot up the knoppix live cd fine

---

### Post by PmDematagoda on 2007-12-02
Why don't you try installing Ubuntu using the [Alternate CD]("http://www.ubuntu.com/getubuntu").

Check the check box near the end of the web page which will allow you to download the Alternate CD.

By the way, the Alternate CD is the text-based installer for Ubuntu, if by any chance you were wondering about what it is:).

---

### Post by Just4 on 2007-12-02
Yeah I've tried the alternate install cd, I got it installed but the desktop hung at a black screen with the mouse cursor... Ir eally want to get ubuntu installed, but I'm just not sure how to get it to not hang on this system

---

### Post by PmDematagoda on 2007-12-02
Try this by booting Ubuntu in Recovery Mode:-

1) Install the Nvidia drivers using:-
```

apt-get install nvidia-glx-new
```

2) After installation reconfigure the X-server using:-
```
dpkg-reconfigure xserver-xorg
```
Select the driver as Nvidia and select any other options you thick are correct.

3) After reconfiguration do:-
```

startx
```
To see if your GUI works.

---

### Post by Just4 on 2007-12-02
I tried that but it says its unable to retrieve it and try apt-get update first, when I do that is says it can't resolve the servers.

I don't think I have a connection under it, I know my NIC works under linux, it works fine in knoppix, so what should I do?

---

### Post by Just4 on 2007-12-02
Bump please, and thanks so much for the help so far.

---

