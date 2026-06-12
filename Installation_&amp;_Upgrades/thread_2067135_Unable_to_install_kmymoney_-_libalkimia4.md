---
title: "Unable to install kmymoney - libalkimia4"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by jleyaoua on 2012-10-06
Hello, 

I am using the Precise version. After the last update, the package management system was broken. I uninstalled Kmymoney to repair it.

Next, I tried to re-install kmymoney. But I got this message :```
 kmymoney depends on libalkimia4; however:   Package libalkimia4 is not installed.
```When I try to install libalkimia4, I got this message : 

```

Dépaquetage de libalkimia4 (à partir de .../libalkimia4_4.3.1-1_i386.deb) ...
dpkg : erreur de traitement de /var/cache/apt/archives/libalkimia4_4.3.1-1_i386.deb (--unpack) : tentative de remplacement de « /usr/lib/pkgconfig/libalkimia.pc », qui appartient aussi au paquet libalkimia 4.3.1-0ubuntu1~ppa6

Aucun rapport « apport » écrit car MaxReports a déjà été atteint

Des erreurs ont été rencontrées pendant l'exécution :
 /var/cache/apt/archives/libalkimia4_4.3.1-1_i386.deb

E: Sub-process /usr/bin/dpkg returned an error code (1)

```Have you got an idea to help me to re-install kmymoney and libalkimia4 ? Thanks !

---

### Post by bra|10n on 2012-10-06
[https://launchpad.net/~claydoh/+archive/kmymoney2-kde4](https://launchpad.net/~claydoh/+archive/kmymoney2-kde4)

---

### Post by jleyaoua on 2012-10-07
Hello, 

Thanks.  Indeed, there was a conflit with a previous version of libalkimia (ppa).

Jean-Marie

---

