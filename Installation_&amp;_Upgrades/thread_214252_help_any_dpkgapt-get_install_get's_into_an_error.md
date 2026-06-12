---
title: "help any dpkg/apt-get install get's into an error"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by RaZer0r on 2006-07-12
whenever I try to install any program using dpkg of apt-get (havent tried the ./configure yet) i get this error.
```

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.2_i386.deb (--unpack):
 unable to open files list file for package `gtk2-engines-mist': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/login_1%3a4.0.13-7ubuntu3.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
rein@ubuntu:~$ sudo dpkg -S gtk2-engines-mist
dpkg-query: unable to open files list file for package `gtk2-engines-mist': Input/output error

```

Anyone any suggestions? I allready tried:
- sudo dpkg -S gtk2-engines-mist
- sudo apt-get dist-upgrade
- sudo apt-get --reinstall install dpkg

tried a reinstall from synaptic.. uninstall, , complete uninstall, none of them did anything that got me forward...

---

