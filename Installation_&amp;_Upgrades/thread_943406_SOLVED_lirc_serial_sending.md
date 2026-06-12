---
title: "SOLVED lirc_serial sending"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by Cyber Source on 2008-10-10
Thanks to Mario!

Problem was sending of infrared signals via serial port and lirc_serial module. I had led's on the actual ir blaster so I could see the lights lighting up when changing channels but it wasn't changing the receiver. A tip from Mario suggested to edit the softcarrier module option for the lirc_serial module. Edited /etc/modprobe.d/lirc-serial and added softcarrier=1 to the options line and all was good! Thanks Mario!

---

