---
title: "[SOLVED] Need help installing ndiswrapper-1.47 in Feisty"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2007-07-17
Hey everyone,

  After some trouble with openSuse erasing my Dapper install, I decided I might as well upgrade since I have nothing left! I downloaded and installed Feisty and found that my wireless card was supposed to work "out of the box" with it. This definitely did not happen!! I have been trying for about a week and a half to get this card working (Linksys WUSB54Gv4). I have been trying to install ndiswrapper-1.47 but am not having luck. Here is what I did:

1. I downloaded ndiswrapper from sourceforge and transferred it via usb thumb drive to my Feisty machine.
2. I untar'd the file and went into it
3. I then ran make distclean (no errors)
4. I  then ran make (no errors)
5. I ran sudo make install (no errors)
6. I went to the WUSB54Gv4 directory of my wireless card after I untar'd that
7. When I run ndiswrapper -v it gives me an error message saying I have version 1.38

module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename: /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586
You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

I don't know if I have 1.38 or how to get rid of it if I do, if that is even the problem. Any help would be much appreciated! Thanks!!

---

### Post by worldgnat on 2007-07-22
I have the same problem. How did you fix it?

-Peter

---

### Post by worldgnat on 2007-07-22
Scratch that - for future reference, what I did was I copied the manually compiled ndiswrapper-1.47 module from ndiswrapper-1.47/driver/ndiswrapper.ko  to /lib/modules/something... (the directory listed under filename in ndiswrapper -v), and it seems to work. It appears that bugs I was experiencing with the 1.38 module (random disconnections etc) have been fixed too, so I think it worked. 

-Peter

---

### Post by JawsThemeSwimming428 on 2007-07-23
Congrats!

---

