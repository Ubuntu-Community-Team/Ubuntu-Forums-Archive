---
title: "Network config trouble"
date: 2020-03-27
forum: Installation &amp; Upgrades
---

### Post by rselvidge on 2020-03-27
xxx.xxx.xxx.xx is not contained in 255.255.255.0/24

installing from GUI and stuck trying to apply Static IP

help me

---

### Post by aljames2 on 2020-03-27
You will need to provide more info.  What are you installing?  You may be trying to assign a static IP address that is not within the static reservation range of that network.

---

### Post by SeijiSensei on 2020-03-27
For local networks you should be using one of the IP blocks set aside for private networks:

10.0.0.0/8
172.16-31.0.0/16
192.168.0-254.0/24

---

