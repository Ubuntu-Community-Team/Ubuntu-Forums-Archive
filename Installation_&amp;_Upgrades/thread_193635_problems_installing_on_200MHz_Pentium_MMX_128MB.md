---
title: "problems installing on 200MHz Pentium MMX 128MB"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by justfred on 2006-06-10
Hi,

possibly taking Xubuntu's manifesto to the extreme, I'm trying to install Xubuntu 6.06 on a 200MHz Pentium MMX with 128MB of RAM (CDROM 4x).

When starting with modified boot options (no splash) and when patient enough (10minutes) the Gnome desktop will eventually appear,

However the mouse (a serial 2 button MS mouse with a DB9 connector as there were in those times)  does not react at all.

Being perseverant of nature I started the install procedure with 'sudo ubiquity' and again with enough patience I can come to step 5 of 6 where the a window appears saying that the partitioner is starting up ... and here I have to admit that I run out of patience : this process seems to be going on for ever and the progress bar seems to get stuck at 42% (the CD is still active and buzzes as usual).

Is there a way to install Xubuntu from the command line (possibly stopping gdm to free up resources) ? Or is the situation really such that Xubuntu will not work on such old hardware ?

Kind regards,
Frederic

---

### Post by Phlosten on 2006-06-10
I believe the ubiquity installer needs at least 192MB ram so maybe the alternate version as opposed to the desktop cd might be the better option.

---

### Post by SkyNet2029 on 2006-06-10
On the other hand, if one were to use the 5.10 installer CD-- (Not sure as to Dapper, since mine was automagic dist-upgrade) you can load the serial-drivers from the Debian-installer menu and your mouse (like mine did) ..should work.

--Edit: This was installed on a Circa. 1996 Dell Optiplex GXMT133 with 64Mb of Ram.(A very ancient Server. Ha). On the limitations portion, It was hobbling with XPpro, fast with KDE and fairly quick with Gnome desktop. The Xubuntu was lightning quick, and strangely, Fluxbox was mind-numbingly slow.

---

### Post by Shinoda on 2007-11-03
> **justfred said:**
> However the mouse (a serial 2 button MS mouse with a DB9 connector as there were in those times)  does not react at all.
See if [this]("http://ubuntuforums.org/showthread.php?t=202972#post1176847") helps.

---

### Post by tubasoldier on 2007-11-03
just to give you a bit of hope i have Debian Sid running on my really old 333mhz laptop with 128mb of ram. I never could get Ubuntu to boot up, even had issues with the alternate disk. But the debian floppy/net install worked real well.

---

### Post by PaganHippie on 2007-11-04
> **justfred said:**
> 
Is there a way to install Xubuntu from the command line (possibly stopping gdm to free up resources) ? Or is the situation really such that Xubuntu will not work on such old hardware ?



Yes, you can install in text-only mode using the Alternate install CD rather than the Live CD; and yes, Xubuntu will work on hardware such as yours -- I have 6.06.1 running on a Pentium 200 MMX with only 64MB of RAM and a 2 GB HDD.  You will get a warning about "low memory mode" while installing, but it *will* work.

Be prepared to have a bit of adventure with manual configuration (I had to fiddle with both video and sound); in my experience the installer doesn't always get everything right the first time, but the machine should be usable even if it wants some tweaking.


Good luck!

---

