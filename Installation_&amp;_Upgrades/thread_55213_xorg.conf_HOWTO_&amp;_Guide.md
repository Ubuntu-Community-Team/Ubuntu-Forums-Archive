---
title: "xorg.conf HOWTO &amp; Guide"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by sorry_name_taken_already2 on 2005-08-07
**I NEED HELP with setting up xorg.conf!**
I think something is wrong with my xorg.conf file. I tried editing it because i found on google that the horizontal and Vertical refresh rates did not match the manufacturer's monitor spec and default colour depth was set at 24. The values were too high and the laptop froze trying to load gdm as a result. My toshiba 4080XCDT uses the, Trident Microsystem Cyber9525 video. Luckily, xorg supports it!

 \\:D/ [http://www.xfree.org/current/trident.4.html](http://www.xfree.org/current/trident.4.html) \\:D/ 
**Supported Hardware**
The trident driver supports PCI, AGP and ISA video cards based on the following Trident chips: 
Blade 
Blade3D, CyberBlade series i1, i7 (DSTN), i1, i1 (DSTN), Ai1, Ai1 (DSTN), CyberBlade/e4, CyberBladeXP, CyberBladeAi1/XP, BladeXP 
Image 
3DImage975, 3DImage985, Cyber9520, Cyber9525, Cyber9397, Cyber9397DVD 
ProVidia 
9682, 9685, Cyber9382, Cyber9385, Cyber9388 
TGUI 
9440AGi, 9660, 9680 
ISA/VLBus 
8900C, 8900D, 9000, 9200CXr, Cyber9320, 9400CXi, 9440AGi These cards have been ported but need further testing and may not work. 

Great but its all greek to me, mate! Howto configure xorg.conf to recognise the onboard video Cyber9525 . I am used to windows where I point to a .inf or install from .exe file and then go to display properties!

Someone teach me how to configure xorg to run X win session or at least a windows manager login screen.

 ](*,) _I am thinking of installing icewm or xpde GUI desktop instead of gnome because i have a slow PII 366 processor._ ](*,) 

I would like help with installing iceWM/Xpde too. Much aprreciated.


Thanks

Andy

---

### Post by varunus on 2005-08-08
Can you post your current /etc/X11/xorg.conf file?  It'll be a lot easier to configure and help you if I have a base to work with.  If not, I can post mine and modify it for your card...

Try XFCE for your processor.  You might like it.  To install XFCE, just get it in Synaptic.  Same with IceWM.  XPDE, I think you have to compile from source...not very friendly.  I don't like it.

---

### Post by e_dson on 2005-08-17
hello! i have a little problem wiht my Toshiba Satellite 1800, Cyberblade Ai1/XP. the driver was correctly defined at xorg.conf ("trident") but xorg crash, changed the value in line "BusID" from "PCI:0:8:0" to "PCI:1:0:0" and,   :-) , Gnome started up great !!! I hope this can help you! Regards from Brazil.

---

