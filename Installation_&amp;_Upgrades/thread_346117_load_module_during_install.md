---
title: "load module during install"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by Baruch on 2007-01-25
I am trying to install Ubuntu 6.10 server on a computer with a USR5416 wireless connection. During the installation it tells me it can't detect a network card, and I might have to load a module manually (Somthing like that, I don't remember the exact wording). How do I do that?

---

### Post by Baruch on 2007-04-11
^BUMP^
(BTW the card uses an acx module/driver (is this the same thing?) of some sort, I think acx111c16, but this might be firmware, not a module. Whats the difference between the two?)

---

### Post by Angry penguin on 2007-04-12
modprobe acx 

to load the module after you login.

---

### Post by Baruch on 2007-04-16
> **Angry penguin said:**
> modprobe acx 

to load the module after you login.

How can I login during Installation?

---

### Post by Angry penguin on 2007-04-17
Dont worry about getting it to work during the install. My computer did the same thing, failed to detect network. Just finish the install, skip the network configuration part or whatever so you can get past it. Then after you get the system installed, login, open a terminal and put the modprobe command in. Then you should be able to go into networking and setup your network device.

Then you might have to add:
acx_pci

to /etc/modules 

To get it to run at startup.

Here is the wiki for troubleshooting wireless if you get stuck:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-f55187f916615b9ab7ecdda4431b3642e533e74e](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-f55187f916615b9ab7ecdda4431b3642e533e74e)

---

