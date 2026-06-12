---
title: "How to remove Wireshark application"
date: 2019-11-23
forum: Installation &amp; Upgrades
---

### Post by janvi2 on 2019-11-23
installed wireshark to listen to the ethernet port using the Ubuntu software rep. After installation, access was denied why I tried

>sudo dpkg-reconfigure wireshark-common
>sudo adduser myname wireshark

after that, no more interfaces are found (only external)
Trying to remove wireshark, the password is requested but nothing happens nor any error message ?

---

### Post by uRock on 2019-11-23
What happens when you run **sudo apt remove wireshark**? Wireshark usually has to be run as root for it to see the interfaces.

---

### Post by janvi2 on 2019-11-23
Your removal works. After new install from the rep, I invoke sudo wireshark what shows eno1 and capture starts

---

