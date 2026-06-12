---
title: "New Installation / X System / VBE Error"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by ShoeUnited on 2006-08-27
Hi all.  I'm new to the whole Ubuntu.  And I've been out of the Linux circuit for a few years. (I found my Linux Bible: Redhat 7.2 O.O)

Anyway, I kept running accross an Error that X System could not load.  The reason was that VBE would not initialize V_BIOS.

After the last oh, 8.5 hours, I figured it out.  LOL  Mostly from dinking around in sudo nano /etc/X11/xorg.conf

The problem was that I'm using an HP Pavillion (533w).  It has integrated video.  So those with integrated video may want to listen up. ^_^

The problem seems to lie in the fact that I also had a PCI ATI card (GF people please check and verify).  What happened was that X11 detected the monitor through the ATI card, but only recognized the First PCI as the valid video driver.  So my integrated Intel video was getting first dibs, (PCI:0:2:0) but my monitor is hooked up to my ATI card.

I cannot disable it completely, there were no jumpers to make the bios and system 'dumb' to the onboard video.  So here's my fix, try it and see for yourself:

First I restarted the machine, and booted into BIOS.  I went to where it said Primary Video Driver [PCI] and changed it to onboard.  I changed that to [Onboard].  I then plugged my monitor cable into my onboard monitor out slot after saving and restarting the computer.

X11 worked out the problem, and now I can finally load live boot! ^_^  So, I'm going to install now, and find the proper drivers for my good video card. lol :mrgreen: 

I hope this helps anyone of you out there.  If you have a mother board with onboard drivers, this may be the fix you need.  I wish setup would detect and write all drivers to X11.  This might be a great feature for the next update. ^_^

-Shoe

---

