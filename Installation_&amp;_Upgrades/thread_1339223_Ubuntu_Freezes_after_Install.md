---
title: "Ubuntu Freezes after Install"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by biloyp on 2009-11-27
I downloaded and installed the newest Ubuntu and my desktop freezes after a minute, how frustrating. I think I will revert to an earier version and wait till this issue is fixed.

---

### Post by albandy on 2009-11-27
try updating it from the tty:
press ctrl+alt+f1
login with your user and password
stop gdm: 
sudo service gdm stop
update the system:
sudo aptitude update
upgrade the system:
sudo aptitude upgrade
reboot the system:
sudo reboot

then test it.

---

