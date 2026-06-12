---
title: "AHHH cant install new packages!"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by Blue Toes on 2008-10-24
whenever i try and install a package i get this error message  (most importantly xorg-driver-fgrlz for graphics support)


Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.14-21.51_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.14-21.51_amd64.deb (--unpack):
 trying to overwrite `/usr/sbin/atigetsysteminfo.sh', which is also in package fglrx64-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.14-21.51_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What do I do?

---

### Post by Kevbert on 2008-10-24
What command are you using to install oackages ?  You may need to use 'sudo' for root privileges. For example
```
sudo apt-get install *package*
```

---

### Post by Blue Toes on 2008-10-24
no i use the sudo command. Ever if i try to install from synaptic the error occurs.  When i open the Update manger i get the message

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

i tried to use the 'fix broken packeges' tool on synaptic but it did nt work either...

---

### Post by Kevbert on 2008-10-25
Via Terminal, try using
```
sudo apt-get install -f
```
This should find and repair any broken packages.

---

### Post by Blue Toes on 2008-10-25
it didn't work.  It just tried to install the same package which is broken and gave me the original error message again

---

### Post by Kevbert on 2008-10-26
Have you tried using the following in terminal
```
sudo dpkg --configure -a
```
See if that works on its own.
The other thing to try is a complete removal of the graphics driver via Synaptic and then try re-installing the package.  It looks like you're trying to resolve an ATI driver problem. You may need to reboot between removal and re-install, it's possible that after the reboot you may end up in low resulution mode, until you've got the driver re-installed.

---

### Post by gurubobnz on 2010-05-03
sudo dpkg --configure -a followed by sudo apt-get -f install worked for me. Cheers!

---

