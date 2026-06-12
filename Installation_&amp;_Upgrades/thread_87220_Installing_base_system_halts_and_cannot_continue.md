---
title: "Installing base system halts and cannot continue"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by icekin on 2005-11-07
I have the following hardware and am trying to do a server-expert install :

Pentium 166 Mhz CPU
32 MB RAM
2 GB Hard disk
Realtek LAN network card

I plan to use this as a web server, nothing more. The install said low RAM, so certain options, like language will be disabled. The install goes okay until the screen where it tries to copy the base packages to the system. At this stage, the packages are copied till 35% and the copying stops. The install screen with the various stages of install comes back. So, I try the same step again, but it again fails to complete.

Why are the packages not being copied to hard disk properly? The CD is alright because its new and I used it to successfully install Ubuntu on another computer. I got the following message when trying to boot from CD :

strange...kswapd0 not stopped

Is this normal? The install still proceeded. I tried running Mandrake 9.3 and that worked (except for video and sound). Anyone have a clue?

Also, if this hardware is not good enough for Ubuntu, is there any other distro I could try, just for running a webserver with a basic window manager like fluxbox or fvwm.

---

### Post by icekin on 2005-11-09
Solution :

I decided to try Debian sarge out. The same problem was there too, it stalled during base package install. Then, I tried the install again, saying no when it asked "This machine may have a PCMCIA card. Do you want to turn on PCMCIA devices?". This time the base packages were all copied fully and I was able to proceed with the partition and finish the install.

I think this will work to solve the same problem on Ubuntu as well.

---

