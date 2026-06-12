---
title: "Dependences error aptitude  - blocking upgrade and install"
date: 2020-04-29
forum: Installation &amp; Upgrades
---

### Post by rgb3000 on 2020-04-29
Hi! 
I have a problem installing o upgrade my Ubuntu 16.04 version

If I give these commands:
sudo apt-get upgrade or
or update or sudo apt-get -f install or dpkg --configure 

I obtain these errors

```

sudo apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze      
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... non riuscita.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 aptitude:i386 : Dipende: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) ma non è installabile
                 Dipende: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) ma non è installabile
                 Dipende: libc6:i386 (>= 2.4) ma non è installato
                 Dipende: libcwidget3:i386 ma non è installabile
                 Dipende: libept1.4.12:i386 ma non è installabile
                 Dipende: libgcc1:i386 (>= 1:4.1.1) ma non è installato
                 Dipende: libncursesw5:i386 (>= 5.6+20070908) ma non è installato
                 Dipende: libsigc++-2.0-0c2a:i386 (>= 2.0.2) ma non è installabile
                 Dipende: libsqlite3-0:i386 (>= 3.6.5) ma non è installato
                 Dipende: libstdc++6:i386 (>= 4.6) ma non è installato
                 Dipende: libtinfo5:i386 ma non è installato
                 Dipende: libxapian22:i386 ma non è installabile
                 Raccomanda: apt-xapian-index:i386 ma non è installabile
                 Raccomanda: libparse-debianchangelog-perl:i386 ma non è installabile
 libdrm-dev : Dipende: libdrm2 (= 2.4.56-1~ubuntu1) ma la versione 2.4.92+git1805251830.c1f2d9~oibaf~x è installata
              Dipende: libdrm-intel1 (= 2.4.56-1~ubuntu1) ma la versione 2.4.83+git1710070630.2ecafc~gd~x è installata
              Dipende: libdrm-radeon1 (= 2.4.56-1~ubuntu1) ma la versione 2.4.83+git1710070630.2ecafc~gd~x è installata
              Dipende: libdrm-nouveau2 (= 2.4.56-1~ubuntu1) ma la versione 2.4.83+git1710070630.2ecafc~gd~x è installata
 libdrm2 : Dipende: libdrm-common (>= 2.4.92+git1805251830.c1f2d9~oibaf~x) ma non è installato
 ppa-purge : Dipende: aptitude
E: Errore, pkgProblemResolver::Resolve ha generato delle interruzioni. Questo potrebbe essere causato da pacchetti bloccati.
E: Impossibile correggere le dipendenze

```


So I can't install or upgrade my system, I can't remove or purge packets.

I tried without success this post 

[https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)

My Pc is a **64bit **one: why is there [B]aptitude:i386?
[/B]Is it possible that I have installed packages for 32bit**? **How  can I fix it?
Have you got ideas?

Thank you in advance

---

### Post by CelticWarrior on 2020-04-29
Welcome.

Before discussing the technical issue I should inform you that this is an English forum so even the terminal output should be in English. Italian is not a problem for me but it will be for many others. The way to produce the output in English is is typing LANG=C then Enter before any other command. This way it will stay in English until you close that terminal window. Please do so when asking for help here.

Now, the technical stuff...
Please confirm you're running standard Ubuntu 16.04. If you're running any other flavor (Kubuntu, Xubuntu, Lubuntu, etc.) be aware they're no longer supported (vanilla Ubuntu LTS has 5 years of support but flavors only 3). 
Yes, it's normal to have "i386" packages as well, this isn't the problem. Many software needs 32-bit libraries so it's normal. You may or may not remember at some point adding the i386 architecture. This isn't the cause of unmet dependencies, at first glance.

Please run:
```
LANG=C
sudo apt update
```
and post here the complete error messages. Meanwhile if you find errors related to PPAs then go ahead and either remove or edit them accordingly and try again.

---

### Post by rgb3000 on 2020-04-29
Thank you for your support

Here is my log
```

sebastiano@sebastiano-OptiPlex-360:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

```

```

sebastiano@sebastiano-OptiPlex-360:~$ sudo apt update
[sudo] password for sebastiano: 
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease
Hit:3 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]       
Ign:5 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu xenial InRelease     
Get:6 http://archive.ubuntu.com/ubuntu xenial-security InRelease [109 kB]      
Hit:7 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu xenial InRelease
Get:8 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]   
Err:9 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu xenial Release       
  404  Not Found [IP: 91.189.95.83 80]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [322 kB]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [276 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5984 B]
Get:13 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [74.9 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [124 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [2464 B]
Get:16 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3328 B]
Get:17 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5324 B]
Reading package lists... Done     
E: The repository 'http://ppa.launchpad.net/mc3man/trusty-media/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```


```

sebastiano@sebastiano-OptiPlex-360:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libc6:i386 (>= 2.4) but it is not installed
                 Depends: libcwidget3:i386 but it is not installable
                 Depends: libept1.4.12:i386 but it is not installable
                 Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                 Depends: libncursesw5:i386 (>= 5.6+20070908) but it is not installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installable
                 Depends: libsqlite3-0:i386 (>= 3.6.5) but it is not installed
                 Depends: libstdc++6:i386 (>= 4.6) but it is not installed
                 Depends: libtinfo5:i386 but it is not installed
                 Depends: libxapian22:i386 but it is not installable
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.56-1~ubuntu1) but 2.4.92+git1805251830.c1f2d9~oibaf~x is installed
              Depends: libdrm-intel1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
              Depends: libdrm-radeon1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
              Depends: libdrm-nouveau2 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
 libdrm2 : Depends: libdrm-common (>= 2.4.92+git1805251830.c1f2d9~oibaf~x) but it is not installed
 ppa-purge : Depends: aptitude
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


```


```

sebastiano@sebastiano-OptiPlex-360:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libc6:i386 (>= 2.4) but it is not installed
                 Depends: libcwidget3:i386 but it is not installable
                 Depends: libept1.4.12:i386 but it is not installable
                 Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                 Depends: libncursesw5:i386 (>= 5.6+20070908) but it is not installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installable
                 Depends: libsqlite3-0:i386 (>= 3.6.5) but it is not installed
                 Depends: libstdc++6:i386 (>= 4.6) but it is not installed
                 Depends: libtinfo5:i386 but it is not installed
                 Depends: libxapian22:i386 but it is not installable
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.56-1~ubuntu1) but 2.4.92+git1805251830.c1f2d9~oibaf~x is installed
              Depends: libdrm-intel1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
              Depends: libdrm-radeon1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
              Depends: libdrm-nouveau2 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
 libdrm2 : Depends: libdrm-common (>= 2.4.92+git1805251830.c1f2d9~oibaf~x) but it is not installed
 ppa-purge : Depends: aptitude
E: Unmet dependencies. Try using -f.


```

```

sebastiano@sebastiano-OptiPlex-360:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libdrm-dev:amd64:
 libdrm-dev:amd64 depends on libdrm2 (= 2.4.56-1~ubuntu1); however:
  Version of libdrm2:amd64 on system is 2.4.92+git1805251830.c1f2d9~oibaf~x.
 libdrm-dev:amd64 depends on libdrm-intel1 (= 2.4.56-1~ubuntu1); however:
  Version of libdrm-intel1:amd64 on system is 2.4.83+git1710070630.2ecafc~gd~x.
 libdrm-dev:amd64 depends on libdrm-radeon1 (= 2.4.56-1~ubuntu1); however:
  Version of libdrm-radeon1:amd64 on system is 2.4.83+git1710070630.2ecafc~gd~x.
 libdrm-dev:amd64 depends on libdrm-nouveau2 (= 2.4.56-1~ubuntu1); however:
  Version of libdrm-nouveau2:amd64 on system is 2.4.83+git1710070630.2ecafc~gd~x.

dpkg: error processing package libdrm-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ppa-purge:
 ppa-purge depends on aptitude.

dpkg: error processing package ppa-purge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptitude:i386:
 aptitude:i386 depends on libapt-pkg4.12 (>= 0.8.16~exp12ubuntu6).
 aptitude:i386 depends on libboost-iostreams1.46.1 (>= 1.46.1-1).
 aptitude:i386 depends on libc6 (>= 2.4).
 aptitude:i386 depends on libcwidget3.
 aptitude:i386 depends on libept1.4.12.
 aptitude:i386 depends on libgcc1 (>= 1:4.1.1).
 aptitude:i386 depends on libncursesw5 (>= 5.6+20070908).
 aptitude:i386 depends on libsigc++-2.0-0c2a (>= 2.0.2).
 aptitude:i386 depends on libsqlite3-0 (>= 3.6.5).
 aptitude:i386 depends on libstdc++6 (>= 4.6).
 aptitude:i386 depends on libtinfo5.
 aptitude:i386 depends on libxapian22.

dpkg: error processing package aptitude:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdrm2:amd64:
 libdrm2:amd64 depends on libdrm-common (>= 2.4.92+git1805251830.c1f2d9~oibaf~x); however:
  Package libdrm-common is not installed.

dpkg: error processing package libdrm2:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgl1-mesa-glx:amd64:
 libgl1-mesa-glx:amd64 depends on libdrm2 (>= 2.4.75); however:
  Package libdrm2:amd64 is not configured yet.

dpkg: error processing package libgl1-mesa-glx:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-ogltrans:
 libreoffice-ogltrans depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package libreoffice-ogltrans (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libgl1-mesa-glx | libgl1; however:
  Package libgl1-mesa-glx:amd64 is not configured yet.
  Package libgl1 is not installed.
  Package libgl1-mesa-glx:amd64 which provides libgl1 is not configured yet.

dpkg: error processing package libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-pdfimport:
 libreoffice-pdfimport depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-pdfimport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-avmedia-backend-gstreamer:
 libreoffice-avmedia-backend-gstreamer depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-avmedia-backend-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.
 libreoffice-impress depends on libreoffice-draw (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-draw is not configured yet.

dpkg: error processing package libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:5.1.6~rc2-0ubuntu1~xenial3); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdrm-dev:amd64
 ppa-purge
 aptitude:i386
 libdrm2:amd64
 libgl1-mesa-glx:amd64
 libreoffice-ogltrans
 libreoffice-core
 libreoffice-calc
 python3-uno
 libreoffice-gnome
 libreoffice-pdfimport
 libreoffice-gtk
 libreoffice-draw
 libreoffice-avmedia-backend-gstreamer
 libreoffice-writer
 libreoffice-impress
 libreoffice-math
 libreoffice-base-core

```

---

### Post by rgb3000 on 2020-04-29
[HTML]Meanwhile if you find errors related to PPAs then go ahead and either remove or edit them accordingly and try again[/HTML]

Unfortunately I can't remove nothing due to dependencies stuff

---

### Post by CelticWarrior on 2020-04-29
You can remove the PPA that shouldn't be there.
[http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) has the name suggests, it's for "Trusty" (14.04) only.
It can be easily removed in many ways. Arguably the easiest one is by opening Software & Updates (or Software Properties ?? in 16.04, I don't remember exactly but that release had a different name, not used before or since). Then in the "Other Software" tab you should find the aforementioned PPA, click it, remove.

This is likely not what will solve the APT mess you're in but it's the first step. We'll troubleshoot from there.

---

### Post by dino99 on 2020-04-29
I highly suspect some conflict with non genuine source(s) like ppa(s)
What to do:
- disable all your ppa(s) then update (synaptic is the easiest way to do it)
- downgrade these package(s)

then the blocking upgrade should have been gone

---

### Post by rgb3000 on 2020-04-29
ok thanks

```


sebastiano@sebastiano-OptiPlex-360:~$ sudo apt update
Hit:1 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                                                    
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                                                 
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease         
Hit:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Get:6 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
Fetched 107 kB in 0s (183 kB/s)                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
654 packages can be upgraded. Run 'apt list --upgradable' to see them.


```


if I upgrade, I have the issue

---

### Post by rgb3000 on 2020-04-29
> **dino99 said:**
> I highly suspect some conflict with non genuine source(s) like ppa(s)
What to do:
- disable all your ppa(s) then update (synaptic is the easiest way to do it)
- downgrade these package(s)

then the blocking upgrade should have been gone

I removed all the ppa in "other Software" but if I upgrade I have the issue

---

### Post by ActionParsnip on 2020-04-29
What is the output of:

```

sudo apt-get -f install

```

Thanks

---

### Post by webaake on 2020-04-29
When reading your logs it seems to me that uninstalling some apps might help. From this:```
 libdrm-dev:amd64
 ppa-purge
 aptitude:i386
 libdrm2:amd64
 libgl1-mesa-glx:amd64
 libreoffice-ogltrans
 libreoffice-core
 libreoffice-calc
 python3-uno
 libreoffice-gnome
 libreoffice-pdfimport
 libreoffice-gtk
 libreoffice-draw
 libreoffice-avmedia-backend-gstreamer
 libreoffice-writer
 libreoffice-impress
 libreoffice-math
 libreoffice-base-core
``` You could try to uninstall the complete Libreoffice and uninstall the app aptitude. And then try again. Begin uninstalling the app aptitude. Take it by steps. Of course, as said earlier, still have those PPA's disabled. When all is ok, you can enable the appropriate PPA's again, and reinstall those apps.

---

### Post by rgb3000 on 2020-04-29
Thank you webaake
Unfortunately I can't uninstall 

sebastiano@sebastiano-OptiPlex-360:~$ sudo apt-get remove libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libreoffice' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libc6:i386 (>= 2.4) but it is not going to be installed
                 Depends: libcwidget3:i386 but it is not installable
                 Depends: libept1.4.12:i386 but it is not installable
                 Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                 Depends: libncursesw5:i386 (>= 5.6+20070908) but it is not going to be installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installable
                 Depends: libsqlite3-0:i386 (>= 3.6.5) but it is not going to be installed
                 Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                 Depends: libtinfo5:i386 but it is not going to be installed
                 Depends: libxapian22:i386 but it is not installable
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.56-1~ubuntu1) but 2.4.92+git1805251830.c1f2d9~oibaf~x is to be installed
              Depends: libdrm-intel1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is to be installed
              Depends: libdrm-radeon1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is to be installed
              Depends: libdrm-nouveau2 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is to be installed
 libdrm2 : Depends: libdrm-common (>= 2.4.92+git1805251830.c1f2d9~oibaf~x) but it is not going to be installed
 ppa-purge : Depends: aptitude
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



> 
Package 'libreoffice' is not installed, so not removed

Actually libreoffice runs correctly ...

---

### Post by rgb3000 on 2020-04-29
sebastiano@sebastiano-OptiPlex-360:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installable
                 Depends: libc6:i386 (>= 2.4) but it is not installed
                 Depends: libcwidget3:i386 but it is not installable
                 Depends: libept1.4.12:i386 but it is not installable
                 Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                 Depends: libncursesw5:i386 (>= 5.6+20070908) but it is not installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installable
                 Depends: libsqlite3-0:i386 (>= 3.6.5) but it is not installed
                 Depends: libstdc++6:i386 (>= 4.6) but it is not installed
                 Depends: libtinfo5:i386 but it is not installed
                 Depends: libxapian22:i386 but it is not installable
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 libdrm-dev : Depends: libdrm2 (= 2.4.56-1~ubuntu1) but 2.4.92+git1805251830.c1f2d9~oibaf~x is installed
              Depends: libdrm-intel1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
              Depends: libdrm-radeon1 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
              Depends: libdrm-nouveau2 (= 2.4.56-1~ubuntu1) but 2.4.83+git1710070630.2ecafc~gd~x is installed
 libdrm2 : Depends: libdrm-common (>= 2.4.92+git1805251830.c1f2d9~oibaf~x) but it is not installed
 ppa-purge : Depends: aptitude
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by webaake on 2020-04-29
Then this:```
aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable...............
```

Uninstall aptitude. It causes a lot of problems and it is "386" for some odd reason. It shouldn't be 386. It is not about if an app works or not. It is about if it causes dependency problems when upgrading, in this case.

---

### Post by rgb3000 on 2020-04-29
> **webaake said:**
> Then this:```
aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installable...............
```

Uninstall aptitude. It causes a lot of problems and it is "386" for some odd reason. It shouldn't be 386. It is not about if an app works or not. It is about if it causes dependency problems when upgrading, in this case.

how can uninstall it, if I obtain the same error when I do 
sudo apt-get uninstall aptitude  

?

---

### Post by rgb3000 on 2020-04-29
> **rgb3000 said:**
> how can uninstall it, if I obtain the same error when I do 
sudo apt-get uninstall aptitude  

?

sorry ... remove

sudo apt-get remove aptitude

---

