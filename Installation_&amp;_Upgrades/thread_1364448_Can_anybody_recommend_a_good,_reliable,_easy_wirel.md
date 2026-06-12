---
title: "Can anybody recommend a good, reliable, easy wireless card?"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Random Guy Surfing Around on 2009-12-25
I want one that can be compatible with Linux and Windows right out of the box. It's really frustrating, my awful Netgear WG111v2 got bent because of the poor manufacturing. What's a good one?

---

### Post by TetonsGulf on 2009-12-25
I use two of the Netgear WG311's with no problems at all.

Takes a minute or two of tinkering, but do the job very nicely.

---

### Post by teage3 on 2009-12-25
Belkin wireless G USB Network adapter works out of the box. Can get it from WallyMart.
Linksys Wireless N works out of the box with Jaunty, But, Karmic you have to blacklist the default driver and install linksys driver from CD.

---

### Post by SuperEngineer on 2009-12-28
[just for info and to help anyone stumbling across this looking for USB as opposed to card answers]

... for many of us who had perfectly working USB wireless adaptors in 9.04 but found they would not connect in 9.10... the easy workaround is:

Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.

Cheers.

---

### Post by SeaJayEmm on 2009-12-29
Linksys wireless network adapters have always been quick easy installs for me in several different distros of Linux, especially Ubuntu.

---

