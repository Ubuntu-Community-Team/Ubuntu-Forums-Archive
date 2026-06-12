---
title: "Xubuntu Install Stars &amp; Stops"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by martnus on 2008-03-03
Greetings All Ubuntu-ers,

   I am a newbie on here, this is only my second (topic) posting so far, so please be gentle....lol

   I am installing Xubuntu on a series of desktops.  These are older Socket 7 FIC and/or AOpen Motherboards that are using a PI 166MHz CPU, and 96MB to 128MB of RAM.

    I have been successful on most installs, getting these to install cleanly and pretty good, but there are certain ones that are giving me a problem.  I have tried replacing Hard Drives and CD-ROM Drives, but it is still the same on each one.

    It starts the install and when it is searching for Hardware Devices, I watch as it gets to 100%, the screen goes blue (with the little gray strip at the bottom) and it just sits there, like it's thinking.  But, it never actually restarts the installation again.

    I was just wondering if anyone out there might have some suggestions of things to look for.  I am not used to using older materials as this, I am more used to Socket 370 and newer Motherboards.  Any help or suggestions would be great, thanks......Martnus

---

### Post by prshah on 2008-03-06
Try installing using "Safe Video Mode" option.

This worked for me because when XUbuntu tried to install in 32-bit (ok 24-bit) color, the whole installation was slow, jerky and failed to complete.

Safe Video mode probably uses 16bit or 256 colours mode.

btw, are you using the "alternate" (textmode) or the "live cd" installer? On such machines, I would recommend you use the Alternate installation CD (they are too underpowered.)

Maybe you would be better off considering a light-weight distro such as PuppyLinux or DamnSmallLinux (DSL).

Cheers,
PRShah

---

