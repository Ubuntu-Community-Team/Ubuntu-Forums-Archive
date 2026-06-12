---
title: "Installation hangs using various methods."
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by markv12 on 2012-05-25
Hi, I'm attempting to install Ubuntu 12.04 64bit for the first time on a custom PC. 

Specs:
Intel Ivy Bridge 3770
Gigabyte GA-Z77 motherboard
16gb G.Skill Ram
Evga GeForce 460 
Crucial M4 SSD

I have produced install CDs and USB installations using instructions on the Ubuntu website (terminal stuff) as well as UNetBootin on both windows and mac machines. Through all of these methods I get to a screen with (sometimes among other commands) "Try Ubuntu without installing", "Check disk for defects", and "Install Ubuntu" I select install ubuntu and I get a blinking _ in the upper or lower left corner and the display blinks about every 4 seconds. At this point it hangs indefinitely as far as I can tell. I really just don't know where to go from here. I don't know how to do a verbose boot, so that might be a place to start. 

Any Suggestions?

---

### Post by ravij96 on 2012-05-25
It might be a bad .iso try downloading the file again from the Ubuntu website and burning another CD. I ran into this same problem today and fixed it by re-downloading the iso. Hope this helps :).

---

### Post by markv12 on 2012-05-25
I downloaded another copy off the website and got the same issue. This time I got the maroon GUI where you can select a language. 
Is it relevant that at the moment my hard drive is formatted for MacOS as this hardware is coming from a hackintosh I gave up on?

I also get the _ with the blinking screen if I select "try linux without installing"

Is there a better place to download than directly off Ubuntu? 

The MD5 matches 

this is really infuriating.

---

### Post by markv12 on 2012-05-25
sometimes the display loses input for a second and comes back like the display driver is getting messed up.

---

### Post by markv12 on 2012-05-26
Well if nothing else, does anyone know how to do a verbose boot?

---

### Post by forcecore on 2012-05-28
I have z77 motherboard too (MSI) and my problem is acpi function causes ubuntu to reset computer, i can only use when acpi is off. Maybe you must disable acpi too with your problem.

---

### Post by justintime2002 on 2012-06-04
I'm currently running into the same problem.  I'm trying to install Ubuntu onto a 128GB M4 using an Asrock Z77 motherboard and can't get past a blank terminal after the options screen.  Very frustrating.

---

### Post by francisco2007 on 2012-06-19
Help!

The same here with Gigabyte Z77-D3H, and Ivy Bridge i7 3770.
I tried to install with 2 DVDs and one CD.
It always hung after the GRUB menu.

Any help would be much appreciated. 

I'm Ubuntu user from 7.04 and I can't install it on my new machine.:(

---

### Post by YannBuntu on 2012-06-20
**@all:** try to boot your installation media adding one or several options (eg "nomodeset", or "acpi=off"): [https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options](https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options)

---

