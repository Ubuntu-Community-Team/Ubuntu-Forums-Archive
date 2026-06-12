---
title: "Stuck on upgrade, need to upgrade bolt and cjs first"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by matrooswolf on 2022-08-13
Hi trying to upgrade from 20.04 to 22.04.1.

Upgrade button does not work, so I dug deeper and this is what I get. Two packages have to be upgraded:```
bolt/focal-updates 0.9.1-2~ubuntu20.04.1 amd64 [opwaardeerbaar van: 0.8-4ubuntu1]
``` and ```
cjs/focal 4.4.0-4 amd64 [opwaardeerbaar van: 4.2.0-1~bionic0]
```
But
```
sudo apt upgrade
``` gives me an error

```
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen
dat u om een onmogelijke situatie gevraagd heeft, of, indien u
de distributie 'unstable' gebruikt, dat sommige benodigde pakketten nog gemaakt moeten worden of uit 'Incoming' verwijderd werden.
De volgende informatie kan misschien helpen de situatie op te lossen:

De volgende pakketten hebben niet-voldane vereisten:
 libcjs0f : Conflicteert met: libcjs0 maar 4.4.0-4 zal geïnstalleerd worden
E: Niet-werkende pakketten

``` it's Dutch, but main thing is, there is a conflict when upgrading cjs between libcjs0f and libcjs0. I can upgrade the package with Synaptic, which will remove libcjs0f and install libcjs0, but I have no idea what the difference is between the packages, what they are used for, why I have the f version, or what will break if I remove it.

So my question is: is it safe to proceed?

I'm really stuck here, so any advice is welcome.

---

### Post by ubfan1 on 2022-08-13
The recommendation for an upgrade is to first remove all additional third party repositories first.  Then apt update and try the upgrade again.

---

