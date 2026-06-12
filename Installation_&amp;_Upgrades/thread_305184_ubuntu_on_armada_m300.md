---
title: "ubuntu on armada m300"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by agherardi on 2006-11-22
I've downloaded and burned the Ubuntu CD ISO image. I'm booting my Compaq Armada M300 from CD, without installing Ubuntu - if possible, I would like to make sure everything works OK before getting rid of Windows XP. Video, sound and mouse are OK, however neither the Ethernet nor the Wireless card (SMC EZConnect G) are working. netstat -i and ifconfig -a show an eth0 and a wifi0 device, both in UP state. However, netstat -r shows no routes. I tried restarting DHCP via the Ethernet card with dhclient eth0. After some time, dhclient says it didn't receive a DHCP whatever packet. On the wireless card, the LINK indicator is not even lit.

Any suggestions would be greatly appreciated!

---

### Post by agherardi on 2006-11-22
Forgot to mention - this is Ubuntu 6.10

---

### Post by K.Mandla on 2006-11-22
Would this be of any help at all?

[http://www.cnbc.cmu.edu/~plaut/m300/](http://www.cnbc.cmu.edu/~plaut/m300/)

It's not Ubuntu-specific, and it's about a year old, but it might give you some ideas about your migration to Linux. 

You might also check the /etc/iftab file and see if the interfaces are properly assigned, and that the /etc/network/interfaces file is also correct. Now that I think of it though, those files might be useful only after a full installation.

---

