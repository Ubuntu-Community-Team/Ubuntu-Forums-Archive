---
title: "Ubuntu 10.04 and 10.10 won't install on Asus P8B75-M Intel i3 3220 3.3GHZ"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by daldude on 2013-01-21
I tried to install Ubuntu 10.04 64-bit Lucid and 10.10 on my new Asus P8B75-M that has a Intel Pentium Core i3-3220 Processor - Dual Core, 3MB L3 Cache, 3.30GHz, Socket H2 (LGA1155) 4 GB of RAM via one DIMM the built in graphics chip on the motherboard a 500 GB SATA Hard Drive hooked to a SATA II (3Gb/s) port. If I try to do  "Try Ubuntu before installing" option with 10.04 and 10.10 after a minute or so I get a message "unable  to find medium  containing a live file system". When I tried to just simply boot 10.04 from my old systems hard drive after a few seconds I get a message from my LCD Monitor that the video signal is out of range but I figured that was because it was set up for different hardware. Also 11.04 has the same problem trying Live mode. 
I tried 12.10 live DVD mode and it worked fine but I hate it's Tablet / Windows 8 like interface that style of interface is great for a tablet but not a PC with a Mouse.:-x
Is 10.04 and 10.10 not compatible with Dual  Core processors or SATA II or is it a compatibility issue with my ASUS Mother Board? 
Is there a way to change 12.10 or 12.04 lts to the old style of 10.04 or 9.04? I really like the MACBUNTU theme I have installed on my old systems 10.04.:)

Thanks in advance for any suggestions or help:)

---

### Post by zvacet on 2013-01-24
I´m not expert,but maybe it is kernel issue.Maybe older kernels don´t have included support for your hardware.Instead of Unity you can choose gnome or something else from login window.

---

### Post by gordintoronto on 2013-01-24
Tried to install from CD? Perhaps a bad burn. But more likely, old OS/new hardware is a bad combination.

In any case, 10.10 is no longer supported, and 10.04 is only good for a couple of months. If you really can't stand Unity, try Xubuntu or Mint with Cinnamon.

---

### Post by bkratz on 2013-01-25
> **daldude said:**
> I tried to install Ubuntu 10.04 64-bit Lucid and 10.10 on my new Asus P8B75-M that has a Intel Pentium Core i3-3220 Processor - Dual Core, 3MB L3 Cache, 3.30GHz, Socket H2 (LGA1155) 4 GB of RAM via one DIMM the built in graphics chip on the motherboard a 500 GB SATA Hard Drive hooked to a SATA II (3Gb/s) port. If I try to do  "Try Ubuntu before installing" option with 10.04 and 10.10 after a minute or so I get a message "unable  to find medium  containing a live file system". When I tried to just simply boot 10.04 from my old systems hard drive after a few seconds I get a message from my LCD Monitor that the video signal is out of range but I figured that was because it was set up for different hardware. Also 11.04 has the same problem trying Live mode. 
I tried 12.10 live DVD mode and it worked fine but I hate it's Tablet / Windows 8 like interface that style of interface is great for a tablet but not a PC with a Mouse.:-x
Is 10.04 and 10.10 not compatible with Dual  Core processors or SATA II or is it a compatibility issue with my ASUS Mother Board? 
Is there a way to change 12.10 or 12.04 lts to the old style of 10.04 or 9.04? I really like the MACBUNTU theme I have installed on my old systems 10.04.:)

Thanks in advance for any suggestions or help:)



I agree about the new interface, that is why I switched to the Mate desktop, it is more familiar.


[http://mate-desktop.org/install/](http://mate-desktop.org/install/)

---

### Post by oldfred on 2013-01-25
I booted with 10.10 until I changed to 12.04, but I installed fallback or gnome-panel in 12.04.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

