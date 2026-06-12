---
title: "Internet &amp; HAL problems upon upgrade"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by ScottinOregon on 2007-12-06
I just updated to 7.10, and now, when the computer starts up, a window appears that reads "Failed to Initialize HAL!" or something to that effect.

Also, I know longer have access to the Internet. The top left icon says "no network connection". I set it to  detect the DHPS network automatically to no avail.

Before the update, Ubuntu had no trouble detecting the network on its own, I don't think I ever made any sort of preference changes.

The computer also works slowly, and seems to lock up as well. Otherwise it's just really, really slow. I'm not sure why.

Can anyone help?

---

### Post by USFMD82 on 2008-01-07
I am having this exact same problem, did anyone find a fix for this?

I went to System-something- restricted Drivers

and i had the following restricted drivers
ATI Accellerated Graphics driver
Software Modem Driver
Firmware Broadcomm 43xx chipset family

when trying to apply or "check mark" them, it would not connect to the internet it come up with "Failed to fetch .....something .us"

so I went and changed it form the us site to the main site, and still no luck then i changed it back.. my comp is running it very slow as well.. it is not the internet not working because i am writing this from the same laptop plugged into the same wall just i loaded in windows and it connected right away..

thanks in advance i will try whatever is mentioned as soon as i see it and report back.. I see this is a common problem but have yet to find the solution, cant fix it without the net it seems :(

---

### Post by USFMD82 on 2008-01-08
Bump.. SOMEONE HELP!! Im already sick of windows!!

---

### Post by inoxllor on 2008-01-11
I got the HAL problem after changing concurrency=none to shell

So I opened the Terminal: ** sudo gedit /etc/sysctl.conf**
and changed concurrency back to none.

---

### Post by lootje2 on 2008-02-15
I had this same HAL! problem, but instead of

> **inoxllor said:**
>   ** sudo gedit /etc/sysctl.conf** 

go here: ** sudo gedit /etc/init.d/rc**

There, find and change the line:
   CONCURRENCY=shell
(back) to:
   CONCURRENCY=none

Save it, close the window and restart your computer.

It worked for me, error message gone, internet connection back.

---

