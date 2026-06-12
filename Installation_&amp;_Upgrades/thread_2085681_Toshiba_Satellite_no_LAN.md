---
title: "Toshiba Satellite no LAN"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by patoly77 on 2012-11-18
I installed Ubuntu Desktop 12.04 LTS on a new Toshiba Satellite C855-S5206 system. All worked well and it detected the WiFi, but there is no eth0 configuration and no LAN network configuration. I installed with network connected to the system, and I know the network connection is good (works on my Mac and PC). Any pointers would be appreciated.

---

### Post by cwsnyder on 2012-11-18
eth0 should be your wired connection, not your wireless connection, which would probably be wlan0.

Are you connected by wired Ethernet connection, or only through WiFi?

---

### Post by patoly77 on 2012-11-18
The wireless is working fine - no problems there. But if I turn off WiFi and connect with a wired connection, there is no LAN definition when I use ifconfig. It is like the network interface was not detected? Thanks...

---

### Post by cwsnyder on 2012-11-18
Please post the output of **lspci -v | grep Ethernet**

---

### Post by patoly77 on 2012-11-18
Output is:

01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10).

---

### Post by cwsnyder on 2012-11-18
Looks like you need the information in the thread [http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126) to get the correct driver, which is evidently not included by default in the kernel yet.

---

### Post by patoly77 on 2012-11-18
Thanks! I'll follow the instructions in that thread.

---

