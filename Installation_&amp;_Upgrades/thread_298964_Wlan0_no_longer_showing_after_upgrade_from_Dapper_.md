---
title: "Wlan0 no longer showing after upgrade from Dapper to Edgy"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by rsinda on 2006-11-13
I am having a problem with Edgy.  Wlan0 is no longer showing even if I do a ifconfig -a .  I have a Dell Laptop with a Dell TrueMobile 1300 in it.  I have been using the NdisWrapper with the drivers.  When I do the Ndiswrapper -l, it lists my driver and says that it is loaded ok with hardware present.  I see that Ndiswrapper is loaded with a modprobe -l.  Does anyone have a suggestion for me?  I'm not new to linux but I am certainly a casual user.  Thanks

---

### Post by jazzwhistle on 2006-11-24
This sounds like my conflict between ndiswrapper and another module. You should be able to work it out for your machine from the info on this thread:

[http://ubuntuforums.org/showthread.php?t=198192](http://ubuntuforums.org/showthread.php?t=198192)

Basically you do lsmod, check if there's another module on the usbcore line that could be conflicting with ndiswrapper, blacklist it as described in that thread, make sure the references to ethx are reset to wlan0, and reboot :)

Cheers

---

