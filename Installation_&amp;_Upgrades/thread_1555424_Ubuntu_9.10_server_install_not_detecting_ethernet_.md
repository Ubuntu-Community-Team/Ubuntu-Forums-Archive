---
title: "Ubuntu 9.10 server install not detecting ethernet card"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by fcmessi on 2010-08-18
I made a bootable USB drive of the Ubuntu 9.10 install disc and booted from it. Upto the network configuration prompt, it worked fine. I configured the network manually since I don't have DHCP setup.

After that, it asked me to select a Ubuntu archive mirror. However, at this point, whatever mirror I select is unable to download the required files. 

I abandoned that install and installed Ubuntu 9.04. Installed fine, but when I booted it up, it refused to detect my network card (which is working fine in Windows 7).

ifconfig does not show an "eth0" connection, and all attempts to connect to the device fail. What could the problem be?

---

### Post by Iowan on 2010-08-18
> **fcmessi said:**
> What could the problem be?It's possible that 9.04 didn't include the proper driver for your NIC. From a terminal (Applications>Accessories>Terminal), check **sudo lshw -C network**

Check **ifconfig -a** to see if eth0 pops up...

---

### Post by fcmessi on 2010-08-19
No, it does not pop up.

---

### Post by fcmessi on 2010-08-19
Bumpity-bump.

---

