---
title: "Cannot Upgrade to natty"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by el-tarado on 2011-05-04
Hi all.

When I try to upgrade from 10.04 to 11.04 I always get this error:

```
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

If I run sudo apt-get dist-upgrade, I get:

```
~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
```

Apparently there's nothing wrong in apt.log, but i cannot upgrade and i don't know how to fix it. Any clue?

---

### Post by lechien73 on 2011-05-04
Hello & welcome to the forums :)

The best advice I can give you is to back up your data and perform a clean install. Having said that, if you did want to try an upgrade, then the second-best piece of advice would try use aptitude for your upgrade:

Install it by:

```
sudo apt-get update
sudo apt-get install aptitude

```
Manually add the new sources:

```
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list
```

Then try perform the upgrade:
 
```
sudo aptitude update
sudo aptitude dist-upgrade

```

---

### Post by el-tarado on 2011-05-04
I wouldn't like to carry out a clean install... it's kind of annoying to configure everything again. So i'll try to upgrade rather than reinstall . i'll keep you posted.

---

### Post by MickAgain on 2011-12-24
Hi!
I'm having the same problem. I followed lechien's suggestions but I still get the same error. It makes it to "Setting new software channels" When it is calculating the changes, I get this error:

```
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```

I would *really* like to get this thing upgraded to the latest release.

---

### Post by MickAgain on 2011-12-24
I went into Synaptic and removed every lib with the name "nvidia" and now mine is upgrading... or at least has moved on to the next phase.

---

### Post by fdrake on 2011-12-24
> **el-tarado said:**
> Hi all.

When I try to upgrade from 10.04 to 11.04 I always get this error:

```
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

If I run sudo apt-get dist-upgrade, I get:

```
~$ sudo apt-get dist-upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```
Apparently there's nothing wrong in apt.log, but i cannot upgrade and i don't know how to fix it. Any clue?

from "man apt-get" (same as for aptitude!)
> 
..........
       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing
           dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. So, dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the
general settings for individual packages.
....


man for "do-release-upgrade"
> 
 Upgrade  the  operating system to the latest release from the command-line.  This is the preferred command if the
       machine has no graphic environment or if the machine is to be upgraded over a remote connection.



if you are looking for a gui do "sudo update-manager --dist-upgrade"

---

