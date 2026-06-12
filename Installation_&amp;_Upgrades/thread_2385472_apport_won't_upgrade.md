---
title: "apport won't upgrade"
date: 2018-02-20
forum: Installation &amp; Upgrades
---

### Post by Baasha on 2018-02-20
I seem to have a bug with my apport program. Whenever I do an automatic upgrade apport reports the following error:
E: /var/cache/apt/archives/apport_2.20.7-0ubuntu3.7_all.deb: subprocess new pre-removal script returned error exit status 1

I have tried the upgrade from Synaptic, but get the same error. I also tried completely removing apport so I could reinstall it, but Synaptic won't allow me to do that either. Other than doing a complete reinstallation of my whole system, is there any other way to fix this?

I am running the Ubuntu 17.10 on a 64 bit machine.

---

### Post by kerry_s on 2018-02-20
try in terminal:
sudo apt clean
sudo apt update && sudo apt -y full-upgrade

---

### Post by Baasha on 2018-02-20
It seems that I get the same error when trying it that way:
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.20.7-0ubuntu3.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kerry_s on 2018-02-20
personally if it was me i would just remove it manually "sudo rm /var/cache/apt/archives/apport_2.20.7-0ubuntu3.7_all.deb"
my reasoning, it's in apt cache, it was download for install by apt. it can be re-downloaded & installed by apt using the update command.

---

### Post by Impavidus on 2018-02-21
> **Baasha said:**
> It seems that I get the same error when trying it that way:
Errors were encountered while processing:
 /var/cache/apt/archives/apport_2.20.7-0ubuntu3.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

It may be helpful to see the full output. The root cause of the error must be in it somewhere.

---

