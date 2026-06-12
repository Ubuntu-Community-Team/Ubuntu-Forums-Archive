---
title: "Package operation failed"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by Graham C Williams on 2012-07-26
Good morning.

REF: "config": /var/cache/debconf/config.dat is locked by another process:
System: 64bit Ubuntu 12.04.

Apart from: 
Please tell me what's going on and how shall I fix it?
Some additional questions:
Why does the list above refer to i386 in places?
and
Why does grub still report an old kernel (Ubuntu, with Linux 2.6.38-8-generic) but I cannot find this kernel in Synaptic?

The 3 extracts below are a bit long but I hope it is of help.

```
Setting up grub-pc (1.99-21ubuntu3.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc

Could not install 'libssl1.0.0'
subprocess installed post-installation script returned error exit status 1

Package operation failed

installArchives() failed: Setting up libssl1.0.0 (1.0.1-4ubuntu5.3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libssl1.0.0:i386 (1.0.1-4ubuntu5.3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.1-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.1); however:
  Package libssl1.0.0 is not configured yet.
dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.99-21ubuntu3.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0 is not configured yet.
dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-human:
 libreoffice-style-human depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-style-tango:
 libreoffice-style-tango depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-style-tango (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-common:
 libreoffice-common depends on libreoffice-style-default | libreoffice-style; however:
  Package libreoffice-style-default is not installed.
  Package libreoffice-style-human which provides libreoffice-style-default is not configured yet.
  Package libreoffice-style is not installed.
  Package libreoffice-style-tango which provides libreoffice-style is not configured yet.
  Package libreoffice-style-human which provides libreoffice-style is not configured yet.
dpkg: error processing libreoffice-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-gb:
 libreoffice-help-en-gb depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-gb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.5.4-0ubuntu1); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
```


A little History.
Upgraded from 11.10 to 12.04 but this left me with a problem in Grub, it had failed to see anything Linux. By booting into a live cd and downloading Grub repair I was able to restore Grub and get things going again. The os-prober does not see the Windows 7 recovery partition. I suspect that Grub is still not correct. Other than an inability to update correctly Ubuntu seems to run fine.

Graham.

---

### Post by dino99 on 2012-07-26
you should check about possible "broken" package(s) into synaptic and fix that first.

then check /etc/apt/sources.list to be sure it only use genuine Precise archives

and clean the system: clean/autoclean/autoremove

and finally update again

if it still does not works, then purge grub-pc and reinstall it

---

### Post by cortman on 2012-07-26
A simple log off/log on will take care of the dpkg lock problem. Explanation and other ways of fixing it available [here]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/").
After that run

```
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```

And see if that fixes the problems.

---

### Post by Graham C Williams on 2012-07-26
Many Thanks:

I have checked the sources.list and that is fine. Spotify (linux) is the only non precise link.

I found no Broken files in Synaptic but found a long list of files in 'Not Installed(Residual config)'.

```
:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
21 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for libssl1.0.0 
```

I can go no further and ask your advice again.

---

### Post by Graham C Williams on 2012-07-27
```
 --station:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
21 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for libssl1.0.0
--station:~$ 
```

---

### Post by Graham C Williams on 2012-07-27
I have also tried to reinstall libssl 1.0.0 via synaptic. I get the same error message then the system stops.
```
 E: Internal Error, No file name for libssl1.0.0 
```

Graham.

---

### Post by cortman on 2012-07-27
You may as well try removing and reinstalling it-

```
sudo apt-get install libssl --reinstall
```

Also try

```
sudo dpkg --configure -a
```

---

### Post by s.fox on 2012-07-27
Please use code tags in future for long terminal outputs. The code tags can be added by clicking: [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG]

Thank you.

---

### Post by Graham C Williams on 2012-07-27
Many Thanks the code suggestion:

```
sudo dpkg --configure -a
```

Has done the trick.
Great:P and thanks for your time.
Graham.

---

### Post by cortman on 2012-07-27
> **Graham C Williams said:**
> Many Thanks the code suggestion:

```
sudo dpkg --configure -a
```

Has done the trick.
Great:P and thanks for your time.
Graham.

Great! Mark the thread [SOLVED] using the thread tools in the upper right, if you would. Good luck!

---

### Post by sunta on 2013-06-06
> **cortman said:**
> Great! Mark the thread [SOLVED] using the thread tools in the upper right, if you would. Good luck!


Ubuntu 12.04.2 LTS
not really:

```
root@dns:~# dpkg --configure -a
root@dns:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra libdbi1 guile-1.8-libs librrd4 ttf-dejavu libjpeg62 php5-mysql
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 61 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for libssl1.0.0
```

---

### Post by sunta on 2013-06-06
solved it myself by:

dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libssl1.0.0          SSL shared libraries

root@dns:/var/cache/apt/archives# dpkg --configure libssl1.0.0
Setting up libssl1.0.0 (1.0.1-4ubuntu5.9) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

