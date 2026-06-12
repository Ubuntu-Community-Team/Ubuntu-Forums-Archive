---
title: "tp-smapi-source failed to install -&gt; kernel-headers missing"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by map84 on 2010-09-12
Hi,

currently I'm using a kernel from kernel-mainline ([http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)), because thermal won't work satisfying with the shipped kernel from ubuntu  and would like to install tp_smapi (including modules hdaps and thinkpad_ec), but the installation failed, because the system pretending, that kernel-headers missing.

doing ```
sudo module-assistant auto-install tp-smapi
```

results in telling the system, that kernel-headers are installed.

```
Getting source for kernel version: 2.6.35-02063504-generic
apt-get install linux-headers-2.6.35-02063504-generic 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Status-Informationen einlesen... Fertig
**linux-headers-2.6.35-02063504-generic ist schon die neueste Version.**

```

but then the upcoming dialog-box of module-assistant telling me, that the kernel-headers are **not** installed and therefore installation of tp_smapi fails.

Can anyone please tell me, how I can solve this?

---

### Post by mark.altern on 2010-10-04
Exactly the same problem, have you solve it?

---

### Post by map84 on 2010-10-05
Not until now. I think the problem would be solved after upgrading to maverick

---

