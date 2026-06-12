---
title: "installing 7.04"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by amoose on 2007-08-11
I have a new dell d630 with vista.  I've  partitioned the hard drive.    I'm a former SUSE loyalist but couldn't get the machine to boot from those disks at all.  The IT guy here said that ubuntu 7.04 would work.  The first problem I encountered was a tty error message: can't access tty: job control turned off.  I found a way to work past that but then I got another error message that although screens were detected there was fatal error starting x.  I've got a shell prompt, but don't know what to do next.  I have a little experience with linux from SUSE, but am no expert.  

Thanks!

---

### Post by chewearn on 2007-08-11
At the shell prompt, type the following command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will allow you to manually set your graphics setting to match your hardware.

---

### Post by amoose on 2007-08-11
Thank you!  I think that my chipset is made by Santa Rosa, though, and is not listed among the x server drivers which came up.


Thank you

---

### Post by Pumalite on 2007-08-11
You should choose 'vesa' as your driver. ( generic; jack of all trades)

---

### Post by amoose on 2007-08-12
Thank you.  I've tried vesa with the coarser resolutions, but no dice.  Is it possible to complete the install from the command line, and, assuming I can get wi-fi or a usb port working, download the appropriate driver?

---

### Post by chewearn on 2007-08-12
AFAIK, support for the new Intel Santa Rosa platform in Feisty 7.04 is spotty :(, since the platform was launched after Feisty release.  There are a few threads in this forum about workarounds, but I have not been following the discussion closely (do a search for "santa rosa").  Otherwise, the best bet is to wait for Gusty release in October.  Sorry.:(

---

