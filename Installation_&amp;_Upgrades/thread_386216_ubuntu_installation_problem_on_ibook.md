---
title: "ubuntu installation problem on ibook"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by clarar on 2007-03-16
Hi,

I'm trying to install Ubuntu on a 2004 iBook, in which I just installed a new third-party hard drive.
I'm using the edgy live cd. When trying to boot from the live cd, in initial startup it gives an error "PCI: cannot allocate resource region 0 on device 0." Then it enters the window manager, and tells me "The panel encountered a problem while loading OAFIID:GNOME_NotificationAreaApplet"; also GNOME_MixerApplet, GNOME_ClockApplet, and several more; it also informs me "Nautilus can't be used now, due to an unexpected error." When I try to install, it tells me that the installer crashed, with a series of errors in /usr/bin/ubiquity ending in "ValueError: microsecond must be in 0..999999"

I also tried the dapper alternate install cd; this goes through most of the installation process okay and then displays similar issues once I get into Gnome.

I also used gparted to wipe the hard drive; no effect.

Since I installed the HD myself and it was my first time dissecting a laptop, I'm suspecting I may have damaged some hardware; but I'm really not sure which part it would be. It also seems surprising that it would "mostly" work (e.g. I can open some programs on the live cd, the alternate cd goes through the installation process seemingly fine, etc...)

Thanks for any advice you may have!

---

### Post by wpshooter on 2007-03-16
Are you sure that you have checked the integrity of your Ubuntu CDs by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you burn your CDs at 4X or less ?

---

### Post by clarar on 2007-03-16
I did verify the CD, but I burned it at > 4x; I'll try making a new CD at 4x or less and see if that helps.
Thanks!

---

### Post by clarar on 2007-03-18
Unfortunately, new, slowly-burned CD has the same issues. Some applications (firefox, gparted, terminal, gimp...) seem to run fine in Gnome from the CD... but I'm still unable to install. 
Any further suggestions what type of problem this could be / what to try next?
thanks!

---

### Post by clarar on 2007-03-26
I figured it out -- my hardware clock had reset itself to 1904, which Gnome can't deal with. Using a failsafe terminal to change the date to something sane fixed the problem!

---

