---
title: "Strange error update message"
date: 2021-02-24
forum: Installation &amp; Upgrades
---

### Post by aughey on 2021-02-24
Just got this fault message on my 20.10 laptop. Havn't a clue what it means but nothing was installed. 

[https://photos.app.goo.gl/CrE32bDPVobd6cBb6](https://photos.app.goo.gl/CrE32bDPVobd6cBb6)

---

### Post by Dennis N on 2021-02-24
I saw the same yesterday from Software Updater. What I did was some terminal stuff. From the terminal history:
1) hold this offending package:
```
sudo apt-mark hold grub-efi-amd64-signed*
```
2) upgrade the rest:
```
sudo apt-get update
sudo apt-get upgrade
```
3) remove the hold on the package:
```
sudo apt-mark unhold grub-efi*
```
4) upgrade again:
```
sudo apt upgrade
```

Upgrade completed without further error.

---

### Post by aughey on 2021-02-25
Many thanks Dennis N

---

### Post by DuckHook on 2021-03-11
Duplicate of: [https://ubuntuforums.org/showthread.php?t=2458624](https://ubuntuforums.org/showthread.php?t=2458624)

Please do not double post as it confuses those trying to help and dilutes community effort.

*Thread Closed.*

---

