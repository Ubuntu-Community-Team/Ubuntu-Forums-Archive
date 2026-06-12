---
title: "dial-up ubuntu 5.10"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by paulmeara on 2005-11-17
I installed ubuntu 5.10 on a Sony Vaio laptop.
Everything looks fine, but the installation doesn't seem to include
a dialler like ppp, so I can't go on-line. Is this normal?

paulmeara

---

### Post by olaf-g on 2005-11-17
I don't use dial-up networking but for a friend I installed ubuntu and I found gnome-ppp quite useful. It's in the menu under *Applications -> Internet -> Gnome PPP*. Otherwise install it:

```
sudo apt-get install gnome-ppp
```

Give it a try. If you need automatic dial up then you have to configure the "Modem connection" under *System -> Administration - > Networking*.

If you can't configure either of them, you must have a problem with your modem. Try out the scanModem script ([guide]("http://www.frankandjacq.com/ubuntuguide/5.04/index.html#identifymodemchipset")) to identify your modem and install suitable drivers (kernel modules, etc.).

Good luck

---

