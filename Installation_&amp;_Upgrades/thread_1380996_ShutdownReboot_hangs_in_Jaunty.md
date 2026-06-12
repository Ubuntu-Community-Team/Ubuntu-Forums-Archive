---
title: "Shutdown/Reboot hangs in Jaunty"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Gatch on 2010-01-14
After a recent upgrade to Jaunty my system hangs after reboot or shutdown with this message on the screen: "Bash [#] Shutting down Cluster Service Manager...."

Tapping the power button loops it back around. Control+Alt+F7 stops at shutting down services.

After reading a number of posts I tried a couple of fixes that had no effect:

> Copy&paste this code in your terminal (all in one line):
sudo update-rc.d -f sendsigs remove && sudo update-rc.d sendsigs start 80 0 6 .
(The last . (dot) is part of the code!)

and

> sudo gedit /etc/init.d/alsa-utils
Search for "stop)" and add immediately below: 
ifconfig eth0 down
ifconfig wlan0 down

You may have guessed I am a copy & paste guy; limited knowledge of code.

---

### Post by Gatch on 2010-01-19
Tried a number of fixes. Gave up. Upgraded to Karmic Koala. 

Everything seems OK.....so far.\\:D/

---

