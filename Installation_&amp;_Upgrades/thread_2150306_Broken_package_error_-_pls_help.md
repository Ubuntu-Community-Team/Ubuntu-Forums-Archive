---
title: "Broken package error - pls help"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by skchomi on 2013-05-31
Please help me with following broken package scenario.

Thanks.


=====================
skchomi@chomi-laptop:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration1 libgtkspell0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-45-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-45-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/975 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 592256 files and directories currently installed.)
Unpacking linux-headers-3.2.0-45-generic-pae (from .../linux-headers-3.2.0-45-generic-pae_3.2.0-45.70_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-45-generic-pae_3.2.0-45.70_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-45-generic-pae/include/config/rfs/accel.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-45-generic-pae/include/config/rfs/accel.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-45-generic-pae_3.2.0-45.70_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
=======================================

---

### Post by Toz on 2013-05-31
> unable to create `/usr/src/linux-headers-3.2.0-45-generic-pae/include/config/rfs/accel.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-45-generic-pae/include/config/rfs/accel.h'): **[COLOR="#FF0000"]No space left on device[/COLOR]**

You seem to be out of available disk space.

---

### Post by skchomi on 2013-05-31
Thanks for reply.

how do I make space?  I cleared - /var/cache/apt/archives but still file system space is still full.

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]skchomi; Hi ! Welcome to the forum.
Get a bit of overhead thus:
[/COLOR]```
sudo apt-get autoclean[COLOR=#000000]
[/COLOR]sudo apt-get autoremove
sudo apt-get clean
```
and now lets look and get an idea of what else one needs to do thus:
```
df -h
```

With that output we get more specific -> pointers pending.[INDENT=2]
there is light when ya get through the tunnel

[/INDENT]

---

### Post by ibjsb4 on 2013-05-31
Its your boot thats full.  Clean out those old kernels.  I use [Synaptic Package Manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") for that, but there are [several ways to do it]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9").

---

