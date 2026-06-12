---
title: "Ubuntu-Tweak and Dependencie Issues as well as Problems with sources.list"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by dr0p3d on 2012-09-21
```
Reading package lists... Done                             
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ precise/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-tweak : Depends: python-lxml but it is not installable
                Depends: python-compizconfig but it is not installable
                Depends: gir1.2-unique-3.0 but it is not installable
E: Unable to correct problems, you have held broken packages.
dr0p3d@DTShells:~$ 

```I have been unable to get the ubuntu tweak installed due to some dependencies. 
and i also have a mixed up sources.list problem it seems. anyone know how i can rebuild this to match the Ubuntu 12.04 LTS Desktop 64 bit setup?

any help would be greatly appreciated and note i run an HP G61 336nr Laptop with this OS... thanks

---

### Post by jerrrys on 2012-09-21
How bout posting your sources.list

gedit /etc/apt/sources.list

or

cat /etc/apt/sources.list

---

