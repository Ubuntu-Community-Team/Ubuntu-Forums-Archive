---
title: "Can not install BRL CAD"
date: 2019-06-14
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2019-06-14
I used the instructions on
[https://linuxg.net/how-to-install-brl-cad-7-28-0-on-ubuntu-18-10-ubuntu-18-04-and-derivative-systems/](https://linuxg.net/how-to-install-brl-cad-7-28-0-on-ubuntu-18-10-ubuntu-18-04-and-derivative-systems/)

I have Ubuntu 16.04 LTS

founder@founder-Aspire-ES1-331:~$ sudo gdebi brlcad*.deb
sudo: unable to resolve host founder-Aspire-ES1-331
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Dependency is not satisfiable: libfontconfig1 (>= 2.12)

Can I fix this problem?

---

### Post by Roland_Msl on 2019-06-14
Just tried:

sudo apt-get install libfontconfig1
sudo: unable to resolve host founder-Aspire-ES1-331
[sudo] password for founder: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libfontconfig1 is already the newest version (2.11.94-0ubuntu1.1).
libfontconfig1 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Seems there is a version problem with Ubuntu 16.04 LTE

---

### Post by Roland_Msl on 2019-06-16
Just tried, but failed:

 sudo gdebi /home/founder/Downloads/libfontconfig1_2.12.6-0ubuntu2_amd64.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done
This package is uninstallable
Breaks existing package 'libfontconfig1-dev' dependency libfontconfig1 (= 2.11.94-0ubuntu1.1)

---

### Post by Impavidus on 2019-06-16
The package you want to install requires libfontconfig1 at least version 2.12. The version in Ubuntu 16.04 is 2.11, so that's not good enough. Ubuntu 18.04 comes with 2.12, Ubuntu 19.04 with 2.13. You cannot install both versions of libfontconfig1 side-by-side and you have other packages depending on libfontconfig1 2.11. You could upgrade those packages too, but that would give you unsupported packages and lead you into dependency hell. To solve this without entering dependency hell, your options are:
- Upgrade to 18.04, or perform a fresh install of 18.04. 19.04 is another possibility, but has shorter support. It's a bit like using a bazooka to kill a mosquito, but you probably want to upgrade to 18.04 someday anyway.
- Install Ubuntu 18.04 in a virtual machine, install your software  there. I don't know if your system is powerful enough for that.
- Try to install your software some other way than using .deb packages. Maybe you can find a snap package. Manually installing your program and libfontconfig1 2.12 may work too, but sounds like a bad idea to me.

---

