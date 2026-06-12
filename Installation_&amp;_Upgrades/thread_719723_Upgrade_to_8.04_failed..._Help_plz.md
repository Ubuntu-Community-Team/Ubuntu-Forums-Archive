---
title: "Upgrade to 8.04 failed... Help plz"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by jalla2000 on 2008-03-09
i tried to upgrade to 8.04 beta by using 

sudo update-manager -d

but i got a lot of error messages and now my screen resolution i whack

and when i do sudo aptitude upgrade > fail.txt

the contents of fail.txt becomes:

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following partially installed packages will be configured:
  bluez-cups cups-pdf cupsys cupsys-driver-gutenprint foomatic-db-hpijs 
  hal-cups-utils hpijs hplip klogd linux-generic 
  linux-restricted-modules-2.6.24-11-generic 
  linux-restricted-modules-generic nvidia-kernel-common pulseaudio rsync 
  sysklogd ubuntu-desktop ubuntu-minimal ubuntu-standard 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up cupsys (1.3.6-1ubuntu1) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups-pdf:
 cups-pdf depends on cupsys (>= 1.1.15); however:
  Package cupsys is not configured yet.
dpkg: error processing cups-pdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on cupsys (>= 1.1.20); however:
  Package cupsys is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
Setting up rsync (2.6.9-6ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing rsync (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on rsync; however:
  Package rsync is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on cupsys; however:
  Package cupsys is not configured yet.
dpkg: error processing bluez-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.8.2-0ubuntu2); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of foomatic-db-hpijs:
 foomatic-db-hpijs depends on hpijs (>> 2); however:
  Package hpijs is not configured yet.
dpkg: error processing foomatic-db-hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on cupsys; however:
  Package cupsys is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-kernel-common (20051028+1ubuntu8) ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing nvidia-kernel-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-11-generic:
 linux-restricted-modules-2.6.24-11-generic depends on nvidia-kernel-common; however:
  Package nvidia-kernel-common is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-11-generic; however:
  Package linux-restricted-modules-2.6.24-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.11.11); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up pulseaudio (0.9.9-1ubuntu2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on cupsys; however:
  Package cupsys is not configured yet.
 ubuntu-desktop depends on cupsys-driver-gutenprint; however:
  Package cupsys-driver-gutenprint is not configured yet.
 ubuntu-desktop depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up sysklogd (1.5-1ubuntu1) ...
 * Stopping system log daemon...       [122G 
[116G[[31mfail[39;49m]
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing sysklogd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on sysklogd; however:
  Package sysklogd is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Setting up klogd (1.5-1ubuntu1) ...
 * Stopping kernel log daemon...       [122G 
[116G[ OK ]
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing klogd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
 cups-pdf
 hplip
 rsync
 ubuntu-standard
 bluez-cups
 cupsys-driver-gutenprint
 hpijs
 foomatic-db-hpijs
 hal-cups-utils
 nvidia-kernel-common
 linux-restricted-modules-2.6.24-11-generic
 linux-restricted-modules-generic
 linux-generic
 pulseaudio
 ubuntu-desktop
 sysklogd
 ubuntu-minimal
 klogd
Setting up rsync (2.6.9-6ubuntu1) ...
Setting up nvidia-kernel-common (20051028+1ubuntu8) ...
Setting up cupsys (1.3.6-1ubuntu1) ...
Setting up pulseaudio (0.9.9-1ubuntu2) ...
Setting up klogd (1.5-1ubuntu1) ...
 * Stopping kernel log daemon...       [122G 
[116G[ OK ]
Setting up sysklogd (1.5-1ubuntu1) ...
 * Stopping system log daemon...       [122G 
[116G[[31mfail[39;49m]
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...

---

