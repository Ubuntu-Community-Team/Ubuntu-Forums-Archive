---
title: "Problem installing 7.10 in Vista 64"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Over1ord on 2007-10-24
I have an intel E6750, Asus IP-35E mobo, 2GB XMS2 memory, 7800GT, and a 320GB hard disc partitioned for Vista 64 and an unallocated space of 15GB which I am trying to install Ubuntu to.  When I run the windows installer I always get an error during setup that says, "Error while trying to execute: bcdedit :".  When I go and try to launch bcdedit manually it opens up extremely briefly and then disappears.  When I use other methods of viewing my boot setup I only find Vista listed.  When I run it from disk at boot it always hangs too.  I have now tried it with the i386 and the 64bit disc and both have the same problem.

Let me know if you can think of anything to try different.

---

### Post by Over1ord on 2007-10-25
Alright, well I got it working, my problems were as follows:

1) I installed vista to a hard drive, replaced the hard drive with another one, installed ubuntu, then plugged them both in and tried to make it work.  It didnt, the best way is to get around this is to have them both plugged in at when doing it or what I ended up doing was reinstalling ubuntu onto a small partition on the primary vista drive.  With this configuration and having the hard drive set to boot first the GRUB loader and everything else worked perfectly.

2) I also set my SATA hard drive that I had to change the setting on in the BIOS.  I set it from auto detect to Large for the detection option.

Once I did these 2 things all my problems went away and everything works great now.

---

