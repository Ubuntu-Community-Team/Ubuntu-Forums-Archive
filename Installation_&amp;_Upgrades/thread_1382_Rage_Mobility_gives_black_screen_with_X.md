---
title: "Rage Mobility gives black screen with X"
date: 2004-10-20
forum: Installation &amp; Upgrades
---

### Post by graham on 2004-10-20
Hi. I've been fiddling for a couple of days with my fresh Ubuntu install. Congratulations to all involved, it's incredibly impressive.

My only problem is that I get a black screen when ever X starts up. My hardware is a Dell Inspiron 5000 which has an ATI Rage Mobility chipset, and should therefore use the ati driver (not the fglrx driver).

Basically, I think I have exactly the same problem as Thom Sanders reported here:

[http://lists.ubuntu.com/archives/ubuntu-users/2004-September/000372.html](http://lists.ubuntu.com/archives/ubuntu-users/2004-September/000372.html)

It would appear as though it's not been fixed yet. I installed from the warty rc disk (13th October) and have upgraded to the latest packages.

I've managed to get a 1280x1024 display out of it using the vesa driver, but I really need to get it to run at 1400x1050 in order to avoid some rather annoying visual artefacts caused by the slightly different aspect ratio. The vesa driver doesn't appear to want to run at 1400x1050, complaining that there are no modes available.

As soon as I start X with the ati driver there's a very short (and almost imperceptible) flicker, before everything stays black. It does that irrespective of the resolution that I've asked it to run at. Disabling DPMS has no visible effect.

A few days ago this same hardware was running Gentoo, using the ati driver, at 1400x1050, so I know it works.

I'd be happy to jump through an indefinite number of hoops to get this fixed, if somebody out there with the knowledge can help me debug it.

Any thoughts?

---

### Post by humdinger70 on 2004-10-21
More than once when trying to install various Linux distributions on my Dell Inspiron 8000 (which has the ATI Rage Mobility M4), it didn't like the VertRefresh of 60 (the default that Xfree or X.org would try after determining it was an LCD screen)  :x 

I just edited the config file so the VertRefresh had a small range (like, 58-62), and it worked fine (mine does 1600x1200). Your range from your Xfconfig-4 (43-72) is way too much.

Also, don't use anything higher than 16 bits for color depth.  :wink:

---

### Post by graham on 2004-10-22
Thanks for the suggestions. I tried changing the VertRefresh but it had no (visible) effect. I've always found that 16 bit is the way forward too...

Any other suggestions?

---

### Post by jwill on 2004-10-29
I also have ( had ) this problem. I added "vga=791" to the end of the kernel entry of /boot/grub/menu.lst.

Now if I could only get my cordless mouse working ....

---

### Post by mickelmac353 on 2005-12-28
I also get a black screen, and I tried the "vga=791" fix; it works when you enter it in the GRUB menu, but it dosent stay and you have to enter it in each time you start the computer (quite tiresome). I tried adding vga=791 to the actual menu file when I get into ubuntu, but then it says I dont have the permissions to edit it. how did u get it to stay?

---

