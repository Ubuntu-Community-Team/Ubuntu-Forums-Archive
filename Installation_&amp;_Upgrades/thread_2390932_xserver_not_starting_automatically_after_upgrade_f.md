---
title: "xserver not starting automatically after upgrade from 17.10. to 18.04. in Kubuntu"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by shizow on 2018-05-03
I upgrade from 17.10. to 18.04., but the upgrade was only finished 97% and than the laptop froze and I manually turned it off.
Now when I boot up the boot up stops after loading network manager and it stops. I can switch with Alt+F2 to a tty window.

It seems that the xserver is not started, there is no Xorg.0.log.
I already tried: sudo apt-get install --reinstall kubuntu-desktop plasma-desktop plasma-desktop-data sddm xorg xserver-xorg-core xserver-xorg-video-intel && sudo dpkg-reconfigure sddm
But that didnt help.

Any suggestions?

UPDATE:
when i switch to tty2, login and enter startx, KDE starts and I am logged in.
so why is xserver not starting automatically?


[ATTACH]279557[/ATTACH]
[ATTACH]279558[/ATTACH]
[ATTACH]279561[/ATTACH]
[ATTACH]279562[/ATTACH]
[ATTACH]279563[/ATTACH]

syslog continues in 1st reply

---

### Post by shizow on 2018-05-03
[ATTACH]279564[/ATTACH]
[ATTACH]279565[/ATTACH]
[ATTACH]279566[/ATTACH]
[ATTACH]279567[/ATTACH]

---

