---
title: "Install 18.04 server LTS without network connection"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by owen18 on 2018-10-08
The latest version of Ubuntu server (18.04) LTS seems to demand network configuration and refuse to boot without it. 

I  have no desire to connect the server in question to the internet for  anything, and have installed previous versions of Ubuntu server without  network no questions asked.  




Is a network connection an absolute requirement for the latest version of Ubuntu server? Or is there something I'm missing?


  The installation cannot proceed past the network configuration page unless an ethernet connection is active

Pls hep.

---

### Post by owen18 on 2018-10-10
Anyone is able to install Ubuntu server (18.04) LTS successfully without network connection?

---

### Post by mastablasta on 2018-10-10
see this bug report: [https://bugs.launchpad.net/subiquity/+bug/1750819](https://bugs.launchpad.net/subiquity/+bug/1750819)

furthermore i would encourage you to add your experience to the launchpad bug report.

also a user reported that using alternate install disk will give you old installer. however from my memory the old installer had issues with UEFI. if you are not using UEFI, then you should be ok i guess.

---

