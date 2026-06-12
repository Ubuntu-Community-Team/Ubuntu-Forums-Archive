---
title: "Broken package manager"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by yannifan on 2011-03-18
Hello

Im trying to install TinyOS package on Ubuntu Maverick.
However during installation, I get the following error

> 
E: /var/cache/apt/archives/avr-gcc-tinyos_4.1.2-20080806_i386.deb: trying to overwrite '/usr/bin/avr-cpp', which is also in package gcc-avr 1
E: /var/cache/apt/archives/binutils-avr_2.20.1-1ubuntu2_i386.deb: trying to overwrite '/usr/bin/avr-size', which is also in package avr-binutils-tinyos 2.17-20080806


apt-get -f install doesnt help. I get the following error

> dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.
(Reading database ... 238615 files and directories currently installed.)
Unpacking avr-gcc-tinyos (from .../avr-gcc-tinyos_4.1.2-20080806_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/avr-gcc-tinyos_4.1.2-20080806_i386.deb (--unpack):
 trying to overwrite '/usr/bin/avr-cpp', which is also in package gcc-avr 1:4.3.5-1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking binutils-avr (from .../binutils-avr_2.20.1-1ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/binutils-avr_2.20.1-1ubuntu2_i386.deb (--unpack):
 trying to overwrite '/usr/bin/avr-size', which is also in package avr-binutils-tinyos 2.17-20080806
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/avr-gcc-tinyos_4.1.2-20080806_i386.deb
 /var/cache/apt/archives/binutils-avr_2.20.1-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help
Thanks

---

### Post by dabl on 2011-03-18
Apt is trying to tell you something, regarding the wisdom of installing a package compiled for some other Linux distribution.  :wink:

However, if you insist and don't mind breaking the package manager, you can try the "--force-all" option.

```
sudo dpkg -i --force-all avr-gcc-tinyos_4.1.2-20080806_i386.deb
```

If your package manager stops working afterward, you might be able to restore it simply by purging that package, and then run 

```
sudo dpkg --configure -a
```


Maybe.

---

### Post by yannifan on 2011-03-20
Hi

I tried the dpkg command but somehow didnt not work

After some more googling, cam across this link
[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

autoremove helped :)

Thank you

---

