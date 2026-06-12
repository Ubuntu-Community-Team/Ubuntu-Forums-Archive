---
title: "WARNING: The following packages cannot be authenticated!"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by ocherno on 2013-02-21
I have compiled sun-java6-jdk package using OAB and created our private repo to distribute it.

When I tried to install sun-java6-jdk package on workstations, I get

```
root@cgta-srv-04v08:~# apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts gsfonts-x11 java-common libxfont1 sun-java6-bin sun-java6-jre xfonts-encodings
  xfonts-utils
Suggested packages:
  default-jre equivs binfmt-support default-jdk-doc sun-java6-source sun-java6-plugin
  sun-java6-fonts ttf-baekmuk ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  gsfonts gsfonts-x11 java-common libxfont1 sun-java6-bin sun-java6-jdk sun-java6-jre
  xfonts-encodings xfonts-utils
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 60.0 MB of archives.
After this operation, 166 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  sun-java6-jre sun-java6-bin sun-java6-jdk
Install these packages without verification [y/N]? 

```

I've added a key that I used to sign the packages on the workstation.

What can be done to get rid of the WARNING message and install the package w/out human interaction. 

Thanks

OB

---

### Post by MAFoElffen on 2013-02-23
Welcome to Ubuntu Forums.

Try this please:
```

sudo apt-get remove debian-keyring debian-archive-keyring
sudo apt-get clean
sudo apt-get update
sudo apt-get -y install debian-keyring debian-archive-keyring

```

---

