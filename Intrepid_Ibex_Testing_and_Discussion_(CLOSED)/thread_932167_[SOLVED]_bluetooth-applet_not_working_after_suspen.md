---
title: "[SOLVED] bluetooth-applet not working after suspend"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by excogitation on 2008-09-28
I bought a Microsoft (yeah I know :-) ) 5000 bluetooth mouse and it works really nice - just when I resume from suspend the bluetooth icon is missing from the taskbar,
and when I kill the bluetooth-applet and try to run it again "nothing" happens.

When I reboot the mouse connects automatically and works fine again.
Also the bluetooth icon shows again.

---

### Post by apiman on 2008-09-29
It happens the same to me. For now, I need to restart the bluetooth service:
#sudo /etc/init.d/bluetooth restart

This prevents me for restarting the PC

---

### Post by excogitation on 2008-09-29
> **apiman said:**
> It happens the same to me. For now, I need to restart the bluetooth service:
#sudo /etc/init.d/bluetooth restart

This prevents me for restarting the PC

Thanks, apiman.
I wanted to file a bug, but it's already known since 8.04.
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/234672]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/234672")

---

