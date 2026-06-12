---
title: "Cant update/remove/install any packages"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by samjad51 on 2011-11-04
Hi,
Whenever i attempt to install or remove a program, i get:

> root@sami-ubuntu978:/home/sami# sudo apt-get remove gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell-extensions-common : Depends: gnome-shell but it is not going to be installed
 gnome-shell-extensions-weather : Depends: gnome-shell but it is not going to be installed
 gnome-tweak-tool : Depends: gnome-shell but it is not going to be installed
 libcaribou0 : Depends: libcaribou-common (= 0.4.1-0ubuntu1~11.10~ricotz0) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



And whenever i try "apt-get -f install" OR "apt-get install -f"
i get:

> root@sami-ubuntu978:/home/sami# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libcaribou0 : Depends: libcaribou-common (= 0.4.1-0ubuntu1~11.10~ricotz0) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


I am trying to remove gnome-shell, as i want to do a fresh installation of it again. However, i cannot update or install any new programs.

Please advise.

Thanks in advance :D

---

### Post by Hakunka-Matata on 2011-11-04
Have you tried using synaptic and listing broken packages, thereby gaining information on how to proceed?

---

### Post by mörgæs on 2011-11-04
By the way, using the root account is generally not a good idea.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

