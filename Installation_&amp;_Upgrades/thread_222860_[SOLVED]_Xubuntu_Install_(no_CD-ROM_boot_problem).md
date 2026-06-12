---
title: "[SOLVED] Xubuntu Install (no CD-ROM boot problem)"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2006-07-25
To install XUbuntu on this old Pentium II (2) machine I have, I had to put the harddrive into a newer AMD Athlon-XP motherboard that supports CD-ROM booting. I installed Xubuntu with no problem... but when I put the harddrive into the old Pentium II, X-server can't load for obvious reason; it installed drivers for the AMD computer not the older Intel one...BASH comes up but unforuntatley I don't know many commands so my question is: using BASH, is there a way to boot to the liveCD or to run through setup again so I can re-install XUbuntu with the proper drivers.


[I'm sorry if this is in the wrong forum, but I couldn't find a XUbuntu forum (after a REALLY quick look) and I figured this could happen to Ubuntu or KUbuntu installations as well.]

---

### Post by altonbr on 2006-07-25
That's embarssing.. it's already a sticky located at:

[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

dpkg --configure -a
dpkg-reconfigure xserver-xorg

---------------------

Does anyone have a better solution for installing XUbuntu on a hard drive that doesn't have the CD-ROM bootable option in thier BIOS?

---

### Post by altonbr on 2006-07-25
Ok, I lied... XUbuntu can't read all of the computer peripherals (although that command above did fix my display problems), I now can't connect to the internet via my DSL connection. It can read my modem though.

Is there a way through the recovery mode, to re-install xubuntu? Remember, I can't reboot to a CD because my BIOS is to old, and I can't put the hard drive in another computer because the setup will install the wrong drivers.

[EDIT] [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto) shows how to install with floppies... it works great by the way.[/EDIT]

Thanks.

-------------------

'sudo pppoeconf' is suggesting to run 'modconf' to find my ethernet card but modconf can't be found... now what?

---

