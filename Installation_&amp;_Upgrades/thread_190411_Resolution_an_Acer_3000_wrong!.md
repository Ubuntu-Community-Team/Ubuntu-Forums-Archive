---
title: "Resolution an Acer 3000 wrong!"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by tkonicz on 2006-06-06
Hi, I wnat to use an new Acer 3003WLM Notbook only with Ubuntu 6.06 - I dont wont to have any Windows on the Machiene. 
The grafics card is (according to manual): SIS M760GX

But there is a greave fault after Installing Ubuntu: The screen resolution shoul de 1200x800, but i have just 1024x768. I took a look at the xorg.conf file, and the 1200x800 resolution was there, as requested by me during installation. The whole screen is nearly unreadalbe- plaes help, for I really dont want to go back to windows.
How to get the native resolution of 1200x800? ](*,) 
thanks
tomasz

---

### Post by bikeboy on 2006-06-06
This must be THE most asked question from new users (not having a go at you). Have a look though your laptop manual if you have it and see if it lists the horiz refresh and very sync rates. It always helps if they do. Otherwise it may require some more fiddling with a config file that I'm not that familiar with.

---

### Post by toLa` on 2006-06-06
I had this problem before installing the fglrx driver for my ATi Radeon x700 card.

Try typing sudo dpkg-reconfigure xserver-xorg and check whether X is using the SiS driver (if such a thing exists). But I had the same problem when using the generic Vesa display driver prior to installing the proper driver for my card.

---

### Post by tkonicz on 2006-06-06
No, there are no "sync" or "refresh" rates in my manual, just the resolution...:-k

---

### Post by tkonicz on 2006-06-06
no i am using just the "vesa" driver in my xorg.conf.

---

### Post by tkonicz on 2006-06-06
You wrote: "But I had the same problem when using the generic Vesa display driver prior to installing the proper driver for my card."

So, how do I install the proper driver for my card? What do I have to do? Will I have to simply change the word "vesa" to "sis" in my xorg.conf
thanks... tomasz
btw, I even searched the sis-homepage, but they had just drivers for SIS740 series, and they seemed to be very old, they were only for redhat 7.1.

---

### Post by xixer on 2006-06-06
try this:
[http://www.ubuntuforums.org/showthread.php?t=190237&highlight=resolution](http://www.ubuntuforums.org/showthread.php?t=190237&highlight=resolution)

---

### Post by bikeboy on 2006-06-06
[QUOTE=tkonicz]So, how do I install the proper driver for my card? What do I have to do? Will I have to simply change the word "vesa" to "sis" in my xorg.conf
thanks... tomasz[/QUOTE]

Try "sudo dpkg-reconfigure xserver-xorg", it will give a list of drivers pretty early on, perhaps there's an sis driver or something else that will work.

---

### Post by stengah on 2006-06-08
u need to adjust the configuration file xorg.conf.

open the prompt and do: sudo gedit /etc/X11/xorg.conf

Find the screen resolution part of the dokument and add the 'missing' resolution ("1280 x 768") in the lines starting with "modes". Do a restart and u should be fine.

Can u please post the file here. I've got an Acer 3000 laptop as well but messed something up in the file so I'd really like to see the contents.

EDIT: nevermind posting the .conf file, I apparently just missed the part of linux being case sensitive;-)

Cheers!

---

### Post by stengah on 2006-06-08
Forgot: PLEASE do a backup of you xorg.conf file before you change it.

Just in case!
:wink:

---

