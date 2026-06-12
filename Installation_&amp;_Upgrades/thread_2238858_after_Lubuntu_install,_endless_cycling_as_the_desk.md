---
title: "after Lubuntu install, endless cycling as the desktop tries to appear"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by timeofday on 2014-08-10
I have an IBM Thinkpad A22m with a 1 GHz processor and 512 MB of RAM. I just inastalled Lubuntu 14.04 on it using the Ubuntu minimal installation ISO and adding the Lubuntu desktop package. (Before that I had Linux mint 9 Xfce on it, which was working fine.)


Here's the problem: the Thinkpad never gets completely done with booting.  The instant it reaches the desktop and shows the wallpaper and mouse pointer, the screen goes black; a few seconds later the wallpaper and pointer appear again and then the screen goes black again; this repeats over and over endlessly.


Everything else I tried works fine: the Ubuntu minimal install went without a hitch, the Grub menus work, and BIOS menus work.


I tried reaching the command line two ways: 1) pressing CTL-ALT-F1 as the desktop was trying to appear (didn't work; the desktop kept cycling), and 2) through Grub, dropping to the root shell; this worked (but I don't know what to do from there, if anything).


I would like to note that I've also tried a Gparted live CD, and as soon as Gparted (which is really a form of Debian) opened to the Gparted desktop, it went through the same sort of endless cycling.  This means that two different distros, one on the HD and one a live CD, both showed the same problem.  (So the HD is not the problem here.)


What should be my next step?

---

### Post by mörgæs on 2014-08-10
From the root shell please run 
```
lspci | grep -i VGA
```
and post the results.

---

### Post by timeofday on 2014-08-10
Here you go:

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Rage Mobility AGP 2x Series (rev 64)

---

### Post by mörgæs on 2014-08-10
It's a very old graphics processor and I think it's unsupported for 14.04. I suggest something 12.04-based; there are some options in the link in my signature.

---

### Post by timeofday on 2014-08-10
Thank you very much -- this is the first explanation that has made sense to me.  I'm going to try LXLE 12.04 and see where that gets me.

---

### Post by mörgæs on 2014-08-10
You're welcome. Please use Thread Tools for marking a thread solved.

---

