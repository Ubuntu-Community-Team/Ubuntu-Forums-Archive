---
title: "Install Java jre through Webmin"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by gabrielviteri on 2010-03-18
Hi I am trying to install Java jre or jdk through Webmin. 
I try to run: **sudo apt-get install  sun-java6-jre**

```
**> sudo apt-get install  sun-java6-jre**
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
And running: **[B]apt-get -f install**[/B]
```
**> apt-get -f install**
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-plugin ia32-sun-java6-plugin ttf-baekmuk
  ttf-unfonts ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
Do you want to continue [Y/n]? Abort.

```

And running :[B] apt-get -f install -y
[/B]```
**> apt-get -f install -y**
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-plugin ia32-sun-java6-plugin ttf-baekmuk
  ttf-unfonts ttf-unfonts-core ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After this operation, 101MB of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
44964 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-16-0ubuntu1.9.04_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace sun-java6-bin 6-16-0ubuntu1.9.04 (using .../sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6-16-0ubuntu1.9.04_all.deb
 /var/cache/apt/archives/sun-java6-bin_6-16-0ubuntu1.9.04_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Also I need to instal unzip package:

```
**Installing package(s) with command apt-get -y  --force-yes -f  install unzip ..**
 
dpkg: dependency problems prevent configuration of sun-java6-fonts:
 sun-java6-fonts depends on sun-java6-jre (>= 6-16-0ubuntu1.9.04); however:
  Package sun-java6-jre is not installed.
dpkg: error processing sun-java6-fonts (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-fonts
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-fonts: Depends: sun-java6-jre (>= 6-16-0ubuntu1.9.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
**.. install failed!**
```

Thanks in advance for your help

---

### Post by phillw on 2010-03-18
Hi and welcome to the forums

After the 1st attempt, it suggested using the -f flag, why did you abort it ? It was asking to get the dependency that it needs.

> The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin

and with the -f

> The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin


Try it again, but allow the -f install to go ahead.

Regards,

Phill.

---

