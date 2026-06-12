---
title: "Unable to Install, Update, or Remove Any Packages"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by nova47 on 2011-04-15
I can't seem to figure out what's going on here. Whenever I use synaptic to attempt to add/remove anything I receive the following error:

(Reading database... 65%dpkg: unrecoverable fatal error, aborting: files list file for package 'dnsmasq-base' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.

I can't figure out how to get rid of the stupid thing lol

---

### Post by Frogs Hair on 2011-04-15
Try the first command and post the output  if there are errors , if not try the second.
```
sudo dpkg --configure -a
``````
sudo apt-get install -f
```

---

### Post by nova47 on 2011-04-15
The first one passed the second didn't after running autoremove.


ghost@ghostcom:~$ sudo dpkg --configure -a
[sudo] password for ghost: 
ghost@ghostcom:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 tuxpaint-plugins-default linux-headers-2.6.35-22-generic
  libsdl-mixer1.2 tuxpaint-data libmikmod2 dkms libvncserver0 netpbm
  linux-headers-2.6.35-22 libnetpbm10 tuxpaint-stamps-default libsdl-pango1
  libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
ghost@ghostcom:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms libmikmod2 libnetpbm10 libsdl-mixer1.2 libsdl-pango1 libsdl-ttf2.0-0
  libsmpeg0 libvncserver0 linux-headers-2.6.35-22
  linux-headers-2.6.35-22-generic netpbm tuxpaint-data
  tuxpaint-plugins-default tuxpaint-stamps-default
0 upgraded, 0 newly installed, 14 to remove and 72 not upgraded.
After this operation, 173MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 65%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'dnsmasq-base' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by nova47 on 2011-04-16
Solved it myself. I had to do a locate on dnsmasq-base, move it somewhere random, purge it with apt-get, and then do the autoremove.

---

