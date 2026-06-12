---
title: "Upgrade Edgy to Gutsy"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by bytecoders on 2008-02-22
Having some problems upgrading from Edgy to Gutsy, I've found that udev breaks libdevmapper and it's not possible to upgrade.


apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
Calculando la actualización... Falló
Los siguientes paquetes tienen dependencias incumplidas:
  udev: Rompe: libdevmapper1.02 (< 2:1.02.08-1ubuntu7) pero 2:1.02.07-1ubuntu2 va a ser instalado
E: Error, pkgProblemResolver::Resolve generó cortes, esto puede haber sido causado por paquetes retenidos.

Any hints?

---

### Post by forestpixie on 2008-02-22
I was under the impression that to upgrade you had to follow versions - so you'd need to  upgrade to feisty first and then to gutsy

---

### Post by RonKZ on 2008-02-23
I just reinstalled edgy, then the upgrades, which showed also a link to upgrade the the next version, but that link failed with a server-error message.  Time for me to just order latest package on DVD, no biggie except for the wasted time to reinstall and re-setup everything

---

### Post by bytecoders on 2008-02-29
Tried to follow versions, same problem if I try upgrading to Feisty.

I've got lot work, and I've put lots of effort in this server. Reinstall and re-setup everything could take me longer than a month. For me it's not really a problem, however my boss don't share this opinion.

Anyway, thanks for your recommendations.

---

### Post by goldenboy on 2008-04-02
Maybe you should try installing the feisty version of libdevmapper1.02 manually. It looks like udev wants at least version 1.02.08 of libdevmapper to be installed and somehow apt-get is not able to solve this dependency automatically...

Fetch the binary package for feisty here

[http://packages.ubuntu.com/feisty/libdevmapper1.02](http://packages.ubuntu.com/feisty/libdevmapper1.02)

and type

```
sudo dpkg -i libdevmapper1.02_1.02.08-1ubuntu10_i386.deb
```

Maybe you need to run

```
sudo dpkg --configure -a
```

first in order to configure the so far installed packages...

I don't really know if this will work, but I think it might be worth a try.

Cheers

---

### Post by Rocket2DMn on 2008-04-02
This thread is a little old now, but since Edgy is about to stop being supported, I would just wait until Hardy is released in April and do a fresh install then, esp. since Hardy is an LTS release.

---

### Post by goldenboy on 2008-04-03
I think the problem might be related to the new name/version of the libdevmapper package in gutsy and hardy respectively. Till ubuntu feisty libevmapper1.02 is available and since gutsy the package is named libdevmapper1.02.1. Furthermore the dependencies of the package have changed.

Actually I don't really get the dependencies of libdevmapper1.02 (feisty). It depends on dmsetup and dmsetup itself again depends on libdevmapper1.02!?!

cheers

---

### Post by zvacet on 2008-04-03
> Actually I don't really get the dependencies of libdevmapper1.02 (feisty). It depends on dmsetup and dmsetup itself again depends on libdevmapper1.02!?!

```
sudo apt-get install  dmsetup libdevmapper1.02
```

If this doesan´t work just swich install order.

---

