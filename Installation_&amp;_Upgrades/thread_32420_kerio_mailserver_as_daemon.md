---
title: "kerio mailserver as daemon"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by lauicus on 2005-05-07
I've installed kerio mailserver on Ubuntu 5.04. (after converting the rpm to a .deb with alien) 
The problem is that when I try to launch the mailserver with 'start-stop-daemon' as a 'non-root' user it simply stops with the message "Cannot start remote admin server on port 44337: TCPIP not available or port already in use". 
The port is not in use, and if I run the server as root everything works fine.

Does anyone know what goes wrong?

---

