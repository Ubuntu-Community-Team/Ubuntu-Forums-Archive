---
title: "Graphics card driver"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by argoz17 on 2012-07-24
So I installed my unrestricted drivers for my nvidia card when i built my ubuntu 12.04 machine...when i rebooted it said on the screen after boot logo "mode unsupported" so i went ahead and reinstalled the OS, anyone know whats up? i have been searching the web trying to find out an answer.
Many thanks for any help.
-------------------------------------
Well Here are my specs.
My monitor is a 27" Samsung LCD TV. I'm using a VGA cable to connect. 
Graphics is a Zotac with Geforce 210 chipset.
Asrock ATX motherboard.
8 gigs of DDR3 RAM
AMD3+ quad core cpu
and 500gig HDD
Desktop I built myself
---------------------
as you can see I have more than enough power for this thing, and under default settings with no driver my rez only gets up to 1360x768
---------------------------

---

### Post by UltimateCat on 2012-07-24
Hi:D
This Zotac website might have the driver your looking for.

[http://www.zotacusa.com/downloads](http://www.zotacusa.com/downloads)
And this site also-
[http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=44&Itemid=506&lang=en](http://www.zotac.com/index.php?option=com_docman&task=cat_view&gid=44&Itemid=506&lang=en)

Hope this helps you

---

### Post by robtygart on 2012-07-25
Why not install nvidia-current :?:

---

### Post by efflandt on 2012-07-25
What do you mean by "installed my unrestricted drivers"?  Default drivers in live/install iso are **nouveau** (which seems to require **nomodeset** for 12.04), and if you have nvidia graphics, **nvidia-current** typically gets installed by default on the installed system.  At least that is what happened for PC in my sig when 1st installed to USB hard drive for testing and when later installed to an internal drive.  No boot parameters were needed after install (when it ended up with nvidia-current).

Without nomodeset for nouveau on 12.04 live/install iso, I would just get black screen with blinking cursor  past the purple screen with symbols at bottom, or after text menu if pressing a key during 1st purple screen for live boot.  So if you somehow avoided automatic install of nvidia-current, and are still using nouveau on an installed system, try nomodeset kernel boot parameter.

11.10 was just the opposite.  In that with nvidia-current installed, my screen would say "no signal" after the grub menu if I did not use nomodeset.

With VGA you will not necessarily get optimum resolution, and I do not even get native 1080p resolution when using DVI with nouveau.  But I do get 1080p automatically using DVI to HDMI cable with nvidia-current.  But I do not know how to add and force a specific resolution with nouveau or nvidia-current (xrandr may not work with nvidia).

---

