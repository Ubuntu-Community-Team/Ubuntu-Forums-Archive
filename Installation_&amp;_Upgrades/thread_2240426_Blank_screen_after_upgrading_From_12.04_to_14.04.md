---
title: "Blank screen after upgrading From 12.04 to 14.04"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by tattushenoi on 2014-08-20
I did 

> sudo apt-get update 

and installed updates on my 12.04 LTS. After which I installed remaining updates via the **update manager** UI. 

I activated the Radeon 7*** series graphics driver [proprietary] using [B]additional driver UI

[/B]Then clicked on get version 14.04 on the UI. It downloaded all the required packages in around an hour and then it was installing the packages.
 
I had to leave while it was continuing. Then when I came back my laptop was closed [lid] so it presumably went to sleep mode. 
I have absolutely no idea what happened in between. But when I opened it again, I saw the desktop background with UBUNTU 14.04 shown as water mark on bottom left corner. 
But nothing else was on the screen. I tried CTRL+ T but that was not coming. I tried CTRL+ ALT+ DEL. But it did not restart. So I forced power off and then restarted. 
Now all I get is a sort of purple blank screen. 

The grub is 3.2.0 67.
AMD A8 processor. I have a windows 7 versions installed along with Ubuntu. 

Hopefully, the 14.04. 1 is installed but the desktop screen is somehow not appearing.  

Please help. I am sort of a newbie [just know some basic stuff] in linux.


[COLOR=#000000]PS:[/COLOR]

[COLOR=#000000]Now its logging and showing desktop. But its getting heated up and I am not able to access anything apart from the terminal. I guess my graphics proprietary drivers need to be installed. But I cant even access additional drivers UI. Please help.[/COLOR]

---

### Post by tattushenoi on 2014-08-20
Dear All,

   Now its logging and showing desktop. But its getting heated up and I am not able to access anything apart from the terminal. I guess my graphics proprietary drivers need to be installed. But I cant even access additional drivers UI. Please help. 

I think I only need to install the graphics drivers. My graphics is [COLOR=#848484][FONT=arial]1 GB AMD Radeon HD 7670M Dedicated 512 MB AMD Radeon HD 7640G Graphics Integrated. 

Please help. Its getting really heated up and shutting off. I cant access additional drivers UI as its hanging. What can I do? [/FONT][/COLOR]

---

### Post by Bashing-om on 2014-08-20
tattushenoi; Tough situation !

The OEM do little to support ubuntu in the realm of hybrid graphics. There is some movement on the opensource front to address the issue.
> 
1 GB AMD Radeon HD 7670M Dedicated 512 MB AMD Radeon HD 7640G Graphics Integrated


[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

Generally we see hybrid graphics as AMD/Intel/Nvidia. rare is it ATI/ATI (radeon) and there may not be many with any experience in your situation.

What you might do as a temporary thing, is see if in bios you can disable one of the graphic's chip sets and install a driver for the chip set in use (??).

Not much help
[INDENT][INDENT]but a push in the right direction.[/INDENT][/INDENT]

---

