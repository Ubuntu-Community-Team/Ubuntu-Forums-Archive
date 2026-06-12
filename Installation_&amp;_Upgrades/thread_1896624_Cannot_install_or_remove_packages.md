---
title: "Cannot install or remove packages"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2011-12-17
Hello all, 

I woke this morning and tried removing some software on my computer. I was greeted by this error.

```
static@static-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

I then ran dpkg and got this

```
static@static-desktop:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/usr/local/var/dpkg/status' for reading: No such file or directory

```

Can anyone think of why this happened and how i can fix it?

---

### Post by dino99 on 2011-12-17
Are you using third party packages like ppa or else ?
 Disable them in case first (might have some conflicts, usually that happen if different distro packages are mixed, like natty/oneiric, or gnome/kde)

So look at your /etc/apt/sources.list

then:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a
( can take a while, be patient & dont stop it before it ended itself)

sudo reboot

---

### Post by slashwannabe94 on 2011-12-17
> **dino99 said:**
> Are you using third party packages like ppa or else ?
 Disable them in case first (might have some conflicts, usually that happen if different distro packages are mixed, like natty/oneiric, or gnome/kde)

So look at your /etc/apt/sources.list

then:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a
( can take a while, be patient & dont stop it before it ended itself)

sudo reboot


I checked my /etc/apt/sources.list file and i don't think anything is wrong with it. 

```
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

So i then ran the commands and received another error. 

```
static@static-desktop:~$ sudo apt-get clean; sudo apt-get autoclean; sudo apt-get autoremove; sudo dpkg-reconfigure -phigh -a
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dpkg-query: failed to open package info file `/usr/local/var/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: acpi-support is not installed.

```

thanks for the help so far man.

---

### Post by dino99 on 2011-12-17
from synaptic: switch to "main server" instead of "gb"

Look for the old /var/lib/dpkg/status file at /var/lib/dpkg/status-old

rename status to status.bak, status.old to status

then update again

if you still have troubles:

sudo rm /var/cache/apt/archives/*

---

### Post by slashwannabe94 on 2011-12-17
> **dino99 said:**
> from synaptic: switch to "main server" instead of "gb"

Look for the old /var/lib/dpkg/status file at /var/lib/dpkg/status-old

rename status to status.bak, status.old to status

then update again

when i tried opening snyaptic i got this error. (see screenshot)

as for the files i did what you asked. status is now status.bak and status-old is now status.

---

### Post by slashwannabe94 on 2011-12-17
synaptic screenshot.

---

### Post by slashwannabe94 on 2011-12-17
when i try to update i now get this error. 

```
static@static-desktop:~$ sudo apt-get update
E: Archive directory /var/cache/apt/archives/partial is missing.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```sorry about this guys, i feel like i'm annoying you all.

---

### Post by dino99 on 2011-12-17
to get more info, glance at /var/log/ folders/files to know about usefull errors

[http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

---

### Post by slashwannabe94 on 2011-12-17
The last three lines in the /var/log/dpkg.log are as follows. 

```
2011-12-17 02:17:00 startup packages configure
2011-12-17 02:17:00 configure linux-image-2.6.32-36-generic 2.6.32-36.79 2.6.32-36.79
2011-12-17 02:17:00 status half-configured linux-image-2.6.32-36-generic 2.6.32-36.79
```

I am currently using the -36 kernel. 

the dpkg.log1 is empty. 

This is all i could find. Should i look at any other logs?

---

### Post by slashwannabe94 on 2011-12-17
I've had some progress. I backed up the /var/lib/dpkg/available and the /var/lib/dpkg/status file. Then renamed the available-old and status-old to just available and status then moved them to the /usr/local/var/dpkg directory. 

I can now run sudo dpkg --configure -a without any errors. 

But when i try to run the apt-get upgrade command it asks me to perform "dpkg --configure -a" again. I then ran the "sudo dpkg-reconfigure -phigh -a" and it now has a new error. 

```
static@static-desktop:~# sudo dpkg-reconfigure -phigh -a
Cannot read status file: No such file or directory at /usr/sbin/dpkg-reconfigure line 149.

```

Is this progress or have i just messed up badly :/ 

Please helps guys. thanks you for the great help so far.

---

### Post by slashwannabe94 on 2011-12-17
Just had this pop up. Hope it gives anyone out there and insight in what is going on with my machine. thanks again.

SlashWannabe94

---

### Post by slashwannabe94 on 2011-12-17
I have added the available and status file to the /var/lib/dpkg directory and can now run "sudo dpkg-reconfigure -phigh -a". But still no luck.

---

### Post by slashwannabe94 on 2011-12-17
Output of "sudo dpkg-reconfigure -phigh -a" 

```
root@static-desktop:/home/static# sudo dpkg-reconfigure -phigh -a 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 27331
 * Starting AppArmor profiles                                                                                                                                                                                 Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                                                                                                       [ OK ]
 * Reloading AppArmor profiles                                                                                                                                                                                Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                                                                                                                                       [ OK ]
stop: Unknown instance: 
start: Job failed to start
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

atd stop/waiting
atd start/running, process 27631
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
avahi-daemon start/running, process 27689
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support                                                                                                                                       [ OK ] 
 * Enabling additional executable binary formats binfmt-support                                                                                                                                        [ OK ] 
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the force-reload(8) utility, e.g. force-reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

update-initramfs: Generating /boot/initrd.img-2.6.32-36-generic
update-alternatives: using /usr/bin/bsd-write to provide /usr/bin/write (write) in auto mode.
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
Note: running MAKEDEV to create CAPI devices in /dev...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.32-36-generic
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.
root@static-desktop:/home/static# 

```

---

