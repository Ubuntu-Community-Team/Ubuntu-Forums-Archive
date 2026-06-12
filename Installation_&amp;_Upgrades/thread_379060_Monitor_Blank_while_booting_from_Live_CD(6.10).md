---
title: "Monitor Blank while booting from Live CD(6.10)"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Joshi.Rohit on 2007-03-08
hi all,

This is the first time Im trying out Ubuntu. So I got the latest version that is out Ubuntu 6.10.

When I started booting through the CD It showed me options for booting of which I selected the 1st option, then A progress Bar was displayed and after it was complete the monitor went Blank.... and showed "HV Freq over range", Hence Im Not able to get to Desktop and Install Ubuntu. I even tried Vesa Mode but was of no use. tried changing resolution through F4 at boot options but i vain..... 

Is there any work around????

My Config:

AMD Athlon X2 3600+
Asus M2NPV VM (Nforce 430)
Geforce 7300GT (PCI-E)
1GB DDR2 RAM
ViewSonic E50 (15")

---

### Post by KainedUK on 2007-03-08
I have the same problem.

I been trying to get this to work for days... i been reading about... and i downloaded the Alternate version of ubuntu. i went into Recovery mode from grub. i typed: sudo nano /etc/X11/xorg.conf

and noticed that nividia was no where to be seen, and "vesa" was already there, so all i changed was the resolution to 1024x768 (safe size to start). and its not working still not working. do i need to do anything else guys? like install the drivers somehow... or is there anything i am doing wrong.?  i really want ubuntu please help


i have:

AMD  3400+
Nvidia Geforce FX 5600 256mb
1GB ddr ram
Hansol H711 ("19")

---

### Post by Kateikyoushi on 2007-03-08
With these newer systems it is more likely you can install ubuntu from the alternate cd.

---

### Post by watson540 on 2007-03-08
you're close ..in xorg.conf the part that says vesa in "" change it to nv , save it, then type init 2 at console. if that dont work change it to nvidia. if that dont work then you have to download the nvidia driver and compile it while in recovery mode. i would reccommend the latter, just cause its guaranteed to work

---

