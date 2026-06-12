---
title: "Lost keyboard and mouse during 10.04 upgrade - what next?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by redicebiker on 2010-05-08
My 10.04 kubuntu upgrade was going swimmingly until the dialog asking to remove old packages came up and I discovered I have no keyboard or mouse (USB). 

I've tried plugging the KB and mouse into different ports with no luck. 

I can't ssh (or telnet) into the machine, but it responds to pings.

Unless there's a better idea out there, I'm ready to hit the reset button.

If I do reboot the machine, what should/can I do to get the installation to pick up from where it left off?

Thanks - RIB

---

### Post by Zorael on 2010-05-08
Boot up in recovery mode, pick network with root, and do package upgrades. You need a working net connection at this point.
```
# dpkg --configure -a
# aptitude update
# aptitude full-upgrade
```
If you're on a wireless and you need to get into a graphical environment to get your net connection up, this can be a bit tricky. Especially if you use WPA/WPA2 encryption.

---

### Post by redicebiker on 2010-05-09
Tried it, and it seemed to finish the install. 

I had rebooted, and everything seemed to work, but I'm sure you saved me from obscure problems down the road.

Thanks - RIB

---

### Post by daehenoc on 2010-05-20
Hi,

I've got the same problem, although I lost my keyboard and mouse by unplugging them after the download was completed, due to little fingers having access to the keyboard and mouse.

I came back to the upgrade a few hours later and the upgrade was up to the 'replace customised file xxxx', and when I plug the keyboard and mouse back in, no keypresses, mouse movement or mouse clicks register in the window manager.

I've got access to the system via SSH, and I can see the dpkg command running with the upgrade process.

I've tried starting hald, restarting udevd, replugging the kb and mouse, and to no avail.  Is there anything I can do to get the interface back, or should I just reboot the box from SSH and do the above?

Thanks,
Greg

---

### Post by daehenoc on 2010-05-20
I took the plunge and restarted the server from SSH.  I rebooted and used a previous kernel to start the computer, and used --configure, update etc and all was well :)

---

