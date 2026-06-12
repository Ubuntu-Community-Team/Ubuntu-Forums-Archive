---
title: "Reinstall networking"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by MikeFinlay2 on 2012-01-04
HI. I recently updated my Ubuntu Linux to 11.10 whereupon I became unable to connect to the internet. Soley down to my own stupidity and ineptitude I ended up uninstalling all my networking. I have a Ubuntu 11.10 installation disk but don't know how resolve my dilemma. I would appreciate any help. Thanks in advance.

---

### Post by gordintoronto on 2012-01-04
How do you connect to the Internet? Eg, Computer --> Ethernet port --> Ethernet cable --> router?

Is it possible for you to be more specific about "uninstalling all my networking?"

Build a list of what you have installed with this command:
dpkg --get-selections "*" > Desktop/applications

I don't know if this will work for sure, but it's one thing you could try: go to [http://packages.ubuntu.com/oneiric/net/](http://packages.ubuntu.com/oneiric/net/) and select "network manager." Download it to a flash drive, and also each of the listed dependencies which do not appear in the "applications" text file. Install all the downloads on the problem system and reboot.

---

