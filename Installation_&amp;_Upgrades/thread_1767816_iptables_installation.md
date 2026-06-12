---
title: "iptables installation"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by janis.briedis on 2011-05-26
Hello, Ubuntu world,

can anyone advise the best practice of installing and setting
the iptables on U 8.04 LTS? currently iptables is not installed
nor as package nor included as kernel module.

with best,
Janis Briedis

---

### Post by zvacet on 2011-05-26
If you use desktop version then it is time to upgrade,because Hardy desktop is not supported any more.Yopu have iptables installed but if you want to make changes try **ufw**.Also,under synaptic>repositories check all under ubuntu software (except source and CD rom) and first two under updates tab.Reload.Nopw you should be able to install any packages releted to iptables and ufw.

---

### Post by janis.briedis on 2011-05-30
Hello, zvacet,
thank you for the reply / advice, but I am using the server version wo gui.
wbr,
Janis Briedis

---

### Post by Frogs Hair on 2011-05-30
This may be useful. [https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

### Post by zvacet on 2011-05-31
@ **janis.briedis**

**UFW** is not GUI application.See [this.]("https://help.ubuntu.com/community/UFW")

---

