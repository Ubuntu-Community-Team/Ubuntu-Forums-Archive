---
title: "how to reinstall vlc after installing FFmpeg?"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by Hari5g900 on 2013-01-03
Hello,
I seriously need help and fast
I installed FFmpeg on my Ubuntu 10.04 system using the usual sudo apt-get install FFmpeg command and I had to install some libraries. But when I watched the installation progress, i saw that it removed vlc and some other software. I thought i would be able to reinstall it but ```
ubuntu@ubuntu-linux:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.8) but it is not going to be installed
       Depends: libvlccore2 (>= 1.0.0~rc1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.0.6-1ubuntu1.8) but it is not going to be installed
E: Broken packages

```
Please help. I seriously need vlc

---

### Post by zvacet on 2013-01-04
```
sudo apt-get -f install
```

---

