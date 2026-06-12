---
title: "I need help with programs like instlux"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by dielois1 on 2006-08-04
I have tried instlux, colinux, lilo, and gujin.  I can't understand any of them I would appriciate it if someone could help me out.

---

### Post by Neobuntu on 2006-08-07
I repectfully suggest you order a Kubuntu CD.
(Click the Kubuntu link before the ship-it link; I just prefer KDE slightly so get ubuntu if you prefer) 

When it arrives (no "burning" a CD to mess up), 'boot" it (you may have to hold down a certain key or change a start up setting to get you particular computer to boot from CD-ROM first before the hard drive.)

Then (assuming you have about >= 256MB RAM (recommended) observe the live (a bit slower on CDROM) Kubuntu; running on your system.

If all is to your liking, just click install and BE CAREFULL (you should have backups of stuff you cn't live without already done). At worse case, you may want to use the built-in and live partition manager to resize your Windows (FAT or NTFS) partition (intall your old Windows first) and this will simply require another reboot of the live/Install Kubuntu CD to "see" the repartitioning (before install to faster hard drive).

At this point, a small (about 10% and decreasing) number of systems may need help with a particular cheaply made wireless card. The BEST solution is, if the Wireless card does not automatically show up as ready to accept your "SSID", then simple replace it with a KNOWN and recomended device for (K)Ubuntu. Intel WIFi cards work well.

TECHNICAL: Yes many poorly suported (previously win-only and anti-competitive chipset maker) (and processor robbing) devices just work anyway (via reverse enginnering.) 

TECHNICAL: Also, you may just choose to use the actual XP driver in (K)Ubuntu via "ndiswrapper" if you're cheap (like me.) You simply have to reselect the XP drivers everytime an automatic "kernel" upgrade comes through. The "ndis-gtk" package alows you to do this with a point and click GUI. The menu name is "Install Windows Drivers." 

Additional ndiswrapper: I would like to add that your poor manufacture device may have a reverse enginneered driver/module in progress and not working right so you simply put it (Example acx when you have "g" card and TI chipset) in the blacklist text file. Also, if you want ndiswrapper come up on boot, put it is the right text file and at the top. "/etc/modules" file I think. REMEMBER, if you have these two modules for the one device, your system may hang. The moral of the story is look for a driver (based on your chipset) before you try ndiswrapper. Again, most of these things just work (TIME SAVINGS) and with ZERO driver setup (just SSID) but you'd better check before buying if you value your time. It's amazing how well ubuntu does with so much differing hardware and I thank the developers for working on ALL popular devices. This is an area where close software can never compete.

(Kubuntu uses a slight different and equally simple GUI for actual wireless set up. Of course you may mix and match Gnome and KDE programs as you wish but having mainly the KDE ones OR mainly the Gnome ones, are just less clutter.)

IN ADDITION: If there's a developing but inferior (locking up) wireless driver in the making, you'll need to blacklist that driver (just put the name in the right text file) and add ndiswrapper instead (so you don't have two driver/modules for the one device.)

The bottom line is, most everything just works and if it doesn't(in now very rare cases), just replace it! It's about $10 and FAR better then what you wind up spending with Windows software. Trust me, if you are new to all this, it's worth it. Get an online deal with tax and shipping included. I personally purcahced a PCMCIA wireless card to $9.99 this way (total; no gas) and it just works (ZERO DRIVER HASSLE). It's Hot plugable as well. 

So ALWAYS check BEFORE buying. Make darn sure ALL your devices are "open" and not Windows only. Never buy Broadcom for example. It's all about the manufacturer.

---

