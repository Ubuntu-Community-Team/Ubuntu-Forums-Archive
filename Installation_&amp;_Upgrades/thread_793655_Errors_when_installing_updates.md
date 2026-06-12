---
title: "Errors when installing updates"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by 14thWarrior on 2008-05-14
I upgraded to Hardy a short while after its release; the upgrade seemed to go well.  Everything is basically working well; but every time I initiate the update manager and install updates, I get error messages.

The error messages seem to be fairly consistent from update to update; furthermore, the errors don't seem to be having any negative impact on the system, so far as I can tell.

They are, however, rather annoying and worrisome.  I'm a relative linux newb, so I neither understand the significance of the error messages, nor know how to correct and eliminate them.  I'm hoping someone can help enlighten me on this issue.

The latest error messages I received are quoted below:

> E: cron: subprocess post-installation script returned error exit status 1
E: rsync: subprocess post-installation script returned error exit status 1
E: ubuntu-standard: dependency problems - leaving unconfigured
E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: hotkey-setup: subprocess post-installation script returned error exit status 1
E: nvidia-kernel-common: subprocess post-installation script returned error exit status 1
E: linux-restricted-modules-2.6.24-16-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: pulseaudio: subprocess post-installation script returned error exit status 1
E: ubuntu-desktop: dependency problems - leaving unconfigured
E: sysklogd: subprocess post-installation script returned error exit status 1
E: ubuntu-minimal: dependency problems - leaving unconfigured
E: klogd: subprocess post-installation script returned error exit status 1


---

### Post by Partyboi2 on 2008-05-14
What happens when you open a terminal (Applications>Accessories>Terminal) and type
```
 sudo apt-get install -f
```
```
sudo dpkg --configure -a
```

Edit: extra command added

---

### Post by 14thWarrior on 2008-05-14
Running *sudo apt-get install -f* results in:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cron (3.0pl1-100ubuntu2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 1
Setting up rsync (2.6.9-6ubuntu2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing rsync (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cron; however:
  Package cron is not configured yet.
 ubuntu-standard depends on rsync; however:
  Package rsync is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Setting up acpid (1.0.4-5ubuntu9) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Setting up hotkey-setup (0.1-17ubuntu21) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 1
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
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-16-generic:
 linux-restricted-modules-2.6.24-16-generic depends on nvidia-kernel-common; however:
  Package nvidia-kernel-common is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-16-generic; however:
  Package linux-restricted-modules-2.6.24-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.16.18); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
Setting up pulseaudio (0.9.10-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on hotkey-setup; however:
  Package hotkey-setup is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
 ubuntu-desktop depends on pulseaudio; however:
  Package pulseaudio is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up sysklogd (1.5-1ubuntu1) ...
 * Stopping system log daemon...                                         [fail] 
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
 * Stopping kernel log daemon...                                         [ OK ] 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing klogd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cron
 rsync
 ubuntu-standard
 acpid
 acpi-support
 hotkey-setup
 nvidia-kernel-common
 linux-restricted-modules-2.6.24-16-generic
 linux-restricted-modules-generic
 linux-generic
 powermanagement-interface
 pulseaudio
 ubuntu-desktop
 sysklogd
 ubuntu-minimal
 klogd
E: Sub-process /usr/bin/dpkg returned an error code (1)


Running *sudo dpkg --configure -a* results in:

> Setting up rsync (2.6.9-6ubuntu2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing rsync (--configure):
 subprocess post-installation script returned error exit status 1
Setting up acpid (1.0.4-5ubuntu9) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Setting up hotkey-setup (0.1-17ubuntu21) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on hotkey-setup; however:
  Package hotkey-setup is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up cron (3.0pl1-100ubuntu2) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing cron (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
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
Setting up pulseaudio (0.9.10-1ubuntu1) ...
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on cron; however:
  Package cron is not configured yet.
 ubuntu-standard depends on rsync; however:
  Package rsync is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-16-generic:
 linux-restricted-modules-2.6.24-16-generic depends on nvidia-kernel-common; however:
  Package nvidia-kernel-common is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-16-generic; however:
  Package linux-restricted-modules-2.6.24-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.16.18); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up sysklogd (1.5-1ubuntu1) ...
 * Stopping system log daemon...                                         [fail] 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing sysklogd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up klogd (1.5-1ubuntu1) ...
 * Stopping kernel log daemon...                                         [ OK ] 
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
		-n: not really
		-f: force
dpkg: error processing klogd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on sysklogd; however:
  Package sysklogd is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rsync
 acpid
 hotkey-setup
 ubuntu-desktop
 cron
 acpi-support
 nvidia-kernel-common
 pulseaudio
 powermanagement-interface
 ubuntu-standard
 linux-restricted-modules-2.6.24-16-generic
 linux-restricted-modules-generic
 linux-generic
 sysklogd
 klogd
 ubuntu-minimal


---

### Post by Partyboi2 on 2008-05-14
Thanks for that, can you now post the output to this command
```
apt-cache policy sysv-rc
```

---

### Post by 14thWarrior on 2008-05-14
The *apt-cache policy sysv-rc* command returned the following:

> 
sysv-rc:
  Installed: 2.86.ds1-38
  Candidate: 2.86.ds1-38
  Version table:
 *** 2.86.ds1-38 0
        100 /var/lib/dpkg/status
     2.86.ds1-14.1ubuntu45 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages


---

### Post by Partyboi2 on 2008-05-14
the version of sysv-rc you have installed is from debian the hardy version is 2.86.ds1-14.1ubuntu45. You will need to downgrade sysv-rc to the Ubuntu version. To do this open up synaptic package manager and search for sysv-rc, then click on the "package" menu and select "Force Version" After you have finished that in a terminal type:
```
sudo apt-get -f install
```Hopefully this will fix the problems you have been having.
If this is successful you may want to remove 2.86.ds1-38 sysv-rc package from /var/cache/apt/archives to prevent future problems.

---

### Post by 14thWarrior on 2008-05-14
Woohoo!  That fixed my problem! :)

You are awesome Partyboi2; thank you very much for the asistance. :)

I didn't find a package file for the debian version 2.86.ds1-38 in the archives folder you noted.  For now I'm not worrying about that; at least I have a better idea of what to be mindful of if this error happens again.

---

