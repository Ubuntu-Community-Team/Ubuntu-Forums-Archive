---
title: "Error: apt-get upgrade"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by mattmcmanus on 2007-04-16
I havent been able to install any new programs or run any updates for two days now. Update Manger won't open, Synaptic goes to install but then just closes the window and doesnt tell me anything about what heppened and when I try to run apt-get upgrade it gives this dkpg: parse error. 

```
matt@minibetty:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  automatix2 linux-headers-2.6.20-15 linux-headers-2.6.20-15-generic
  linux-image-2.6.20-15-generic linux-libc-dev linux-source-2.6.20
  update-manager update-manager-core
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/82.4MB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 8302 package `xserver-xorg-video-savage':
 field name `bl' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I was wondering if anyone else has run into this.

---

