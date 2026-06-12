---
title: "Installing Feisty with a 8600 GT"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by Bakudan on 2007-08-01
Alright, long story short I bought a bunch of new parts, put them together, installed XP, spent about 10 minutes there before deciding I couldn't part with my precious Ubuntu. After about 7 months of use as my only OS I simply can't part with it. Here is what is inside my computer:

-ASUS M2N-E SLI Motherboard
     -AMD socket AM2
    -DDR2 800
    -Dual-Core ready
    -SLI ready
-AMD Athlon 64-bit x2 5400+ Processor
-2 GB nVidia DDR2 800mhz RAM
-GeForce 8600 GT XFX (two of them in SLI configuration)

Now when I try to install Feisty Fawn 64-bit desktop edition it starts the install and I see the Ubuntu "loading bar" but after filling the whole bar the screen simply goes blank and the monitor goes into standby mode. I tried booting into safe graphics mode specifying resolutions as low as 640x480 and it still fails but it brings me to a blue screen with a grey box informing me that the x server failed to start, and displays the following:
```

X Windows system Version 7.2.0
Release Date 22 Jan 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 12 06:17:24 UTC 2007 x86_64
         Before reporting problems, check http://wiki.x.org to make sure you have the latest version.
Module Loaded present
Markers: (--) probed, (**) from the config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", time: Wed Aug 1 23:20:23 2007
(==) Using config file: "etc/X11/xorg.conf"
(WW) NV: no matching Device section for instance (BusID PCI:5:0:0) found
(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have usable configuration.

Fatal Server error:
No Screens Found
```

Then:

```
The X Server is now disabled. Restart GDM when it is configured correctly.
```

It then then proceeds to drop me into the unix prompt. I'm no linux genius but my first guess what that my cards were too new for the install CD to recognize, so I tired to install and enable some more recent drivers using the following commands:

```

sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig --no-composite

```

However, I am not even sure that I'm loading the right driver. Because afterwards I still cant startx, it just tells me:

```
The x server is disabled, please restard the GDM.
```

Then it promptly reboots.

I can bring up the xorg.conf file if it would help, but its a mighty amount of stuff to type. Any ideas?

---

### Post by Pumalite on 2007-08-01
Try with only one graphics card. Post back with results.

---

### Post by fcigoi on 2007-08-02
Your problem looks a lot like mine....different config but same video card.
There's a sticky post in "Hardware and Laptops" that might be of help, although I myself am still half way through due to other issues.

---

### Post by Bakudan on 2007-08-02
Ok, I figured it out yesterday, and here is what happened. 

Turns out that when you boot up with the ASUS motherboard it identifies the 8600 GT XFX card at the PCI 5:0:0 as the primary and thats where you see all the boot up menus and the live CD startup processes. However, when Ubuntu attempts to identify a screen to create an x session on it scans the PCI slots by ascending order, so it saw the 8600 GT XFX card at address PCI 4:0:0, rather than the primary card, thus the problem.

So I rebooted the machine and went through the live cd boot again I plugged a monitor into the first DVI port on the secondary card, Ubuntu preformed its startup on the PCI 5 screen and created X on the PCI 4 screen. Counter intuitive, but it worked.

Now all that I have left is installing the drivers for the video cards and getting SLI to work correctly.

---

### Post by dabl on 2007-08-02
You're going to need the newest (100.14.11) Nvidia driver to run those 8600s.  Either get it from Nvidia's site, or else use Envy.  Somewhere on this forum is a post that provides a couple of "extra steps" for the 8000-series cards, or at least some of them. :)

---

### Post by gamerteck on 2007-10-06
> **Bakudan said:**
> Ok, I figured it out yesterday, and here is what happened. 

Turns out that when you boot up with the ASUS motherboard it identifies the 8600 GT XFX card at the PCI 5:0:0 as the primary and thats where you see all the boot up menus and the live CD startup processes. However, when Ubuntu attempts to identify a screen to create an x session on it scans the PCI slots by ascending order, so it saw the 8600 GT XFX card at address PCI 4:0:0, rather than the primary card, thus the problem.

So I rebooted the machine and went through the live cd boot again I plugged a monitor into the first DVI port on the secondary card, Ubuntu preformed its startup on the PCI 5 screen and created X on the PCI 4 screen. Counter intuitive, but it worked.

Now all that I have left is installing the drivers for the video cards and getting SLI to work correctly.

This worked for me. I have an SLI setup with a pair of 7800gtx's. Kept the monitor plugged into the first DVI port on the 1st vid card. When I knew it was booting successfully plugged it into the 1st DVI port on the second card.  

Beautiful.. thanks Bakudan :guitar:!

---

