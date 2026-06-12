---
title: "fail to install envfs"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by tomerbd on 2013-12-11
Hi

I'm not sure what to do

> $ sudo apt-get install encfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 encfs : Depends: libboost-serialization1.49.0 (>= 1.49.0-1) but it is not installable
         Depends: libboost-system1.49.0 (>= 1.49.0-1) but it is not installable
E: Unable to correct problems, you have held broken packages.


> $ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring


---

### Post by Bashing-om on 2013-12-11
tomerbd; Hi !

Let's see if we can find out why the package manager is unhappy.
Post back the output of terminal commands:
```

dpkg -l encfs
dpkg -l libboost-serialization
fpkg -l libboost-system
apt-cache policy libboost-serialization
apt-cache policy libboost-system

```

A thought, did you update/upgrade prior to attempting the install of "encfs" ?

[INDENT][INDENT]The chase is afoot
[/INDENT][/INDENT]

---

### Post by tomerbd on 2013-12-16
Hi

Since then I upgraded to 13.10 and installed successfully.  (though now i have a different problem where i cant use google chrome iwth 32 bit java jdk sun oracle).

---

### Post by Bashing-om on 2013-12-16
tomerbd;
Pleased you are up and running,
As to the java situation, I have no experience with that at all, open another thread with that topic and those who do know will see.

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

