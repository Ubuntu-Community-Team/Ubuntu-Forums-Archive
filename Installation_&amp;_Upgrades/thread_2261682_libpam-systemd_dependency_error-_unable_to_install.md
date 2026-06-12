---
title: "libpam-systemd: dependency error- unable to install any packages anymore"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by tomschaack on 2015-01-20
```
USERBLA:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 libpam-systemd : Depends: systemd-services (= 204-5ubuntu20.3)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

```
username:/$ sudo apt-get install systemd
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpam-systemd : Depends: systemd-services (= 204-5ubuntu20.3)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```
Hi there, I crawled whole google and couldn't find help that solved the problem. Ever since Ubuntu 14.04, any apt installation is broken, because of the libpamd errors. I somehow managed to upgrade to 14.10, but I guess maaaaany packages are broken or not updated.

I can't install any package anymore, because of that error.
The only broken package seems to be this one. I also tried in synaptic to just upgrade or remove it, always get's me the same error. "too many errors" etc etc. 

Where to start fixing it ? Just too annoying, as it's a server where i'm running my emailserver, teamspeak etc.....

---

### Post by tomschaack on 2015-01-21
noone has an idea ? :(:confused:

---

### Post by Bashing-om on 2015-01-21
tomschaack; Hello;

I would start by looking at what is installed and what the system says are options:
```

dpkg -l systemd-services
apt-cache policy systemd-services

```

Presently there is this situation:
> 
The following packages have unmet dependencies:
 libpam-systemd : Depends: systemd-services (= 204-5ubuntu20.3)
 A very old package. Even in  14.04 I have :
> 
systemd-services:
  Installed: 204-5ubuntu20.9
  Candidate: 204-5ubuntu20.9


So, the hunt is on as to what is holding ' systemd-services " to that lower version.
Start with what depends on '  systemd-services ' ???
```

apt-cache depends systemd-services

``` anything out-of-place ?

[INDENT][INDENT]what does it take to keep
[INDENT][INDENT][INDENT]a dependency like you
[INDENT][INDENT][INDENT][INDENT][INDENT]satisfied[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by tomschaack on 2015-01-21
i've purged/removed the libpam-system and tried the following...if this helps. to answer your depend question, the result seems weird:
```
apt-cache depends  systemd-services<systemd-services>
```

What I've done before:





```
 dpkg --force-all -P libpam-systemd
dpkg: libpam-systemd:amd64: dependency problems, but removing anyway as you requested:
 policykit-1 depends on libpam-systemd.
 ubuntu-gnome-desktop depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is to be removed.
 pulseaudio depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is to be removed.
 udisks2 depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is to be removed.
 xubuntu-desktop depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is to be removed.
 gdm depends on libpam-systemd; however:
  Package libpam-systemd:amd64 is to be removed.


(Reading database ... 292349 files and directories currently installed.)
Removing libpam-systemd:amd64 (204-5ubuntu20.3) ...
Purging configuration files for libpam-systemd:amd64 (204-5ubuntu20.3) ...
Processing triggers for man-db (2.7.0.2-2) ...
(root@jigo)-(~) $ apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libidl0 liborbit2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpam-systemd systemd
Suggested packages:
  systemd-ui
The following NEW packages will be installed:
  libpam-systemd systemd
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
715 not fully installed or removed.
Need to get 0 B/1,341 kB of archives.
After this operation, 6,203 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up sysv-rc (2.88dsf-41ubuntu18) ...
info: Reordering boot system, log to /var/lib/insserv/run-20150121T2109.log
error: Something failed while migrating.


error: Unable to migrate to dependency based boot sequencing.


See /wiki.debian.org/LSBInitScripts/DependencyBasedBoot for
more information about dependency based boot sequencing. To
reattempt the migration process run 'dpkg --configure sysv-rc'.


dpkg: error processing package sysv-rc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on sysv-rc | file-rc; however:
  Package sysv-rc is not configured yet.
  Package file-rc is not installed.


dpkg: error processing package initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on initscripts; however:
  Package initscripts is not configured yet.


dpkg: error processing package util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of e2fsprogs:
 e2No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                       No apport report written because MaxReports is reached already
                                                         fsprogs depends on util-linux (>= 2.15~rc1-1); however:
  Package util-linux is not configured yet.


dpkg: error processing package e2fsprogs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sysv-rc
 initscripts
 util-linux
 e2fsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)
 apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gdm : Depends: libpam-systemd but it is not installed
 policykit-1 : Depends: libpam-systemd but it is not installed
 pulseaudio : Depends: libpam-systemd but it is not installed
 ubuntu-gnome-desktop : Depends: libpam-systemd but it is not installed
                        Recommends: usb-creator-gtk but it is not installed
 udisks2 : Depends: libpam-systemd but it is not installed
 xubuntu-desktop : Depends: libpam-systemd but it is not installed
                   Recommends: indicator-application but it is not installed
                   Recommends: indicator-messages but it is not installed
                   Recommends: xfce4-power-manager but it is not installed
E: Unmet dependencies. Try using -f.
USERNAME(~) $ apt-get install libpam-systemd
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libpam-systemd : Depends: systemd (= 208-8ubuntu8.2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



```


ok, all depends on systemd


when i then apt-get install systemd....i get the other dependencies !!! It's turning in a circle----what the hell..
```
 apt-get install systemd
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gdm : Depends: libpam-systemd but it is not going to be installed
 policykit-1 : Depends: libpam-systemd but it is not going to be installed
 pulseaudio : Depends: libpam-systemd but it is not going to be installed
 ubuntu-gnome-desktop : Depends: libpam-systemd but it is not going to be installed
                        Recommends: usb-creator-gtk but it is not going to be installed
 udisks2 : Depends: libpam-systemd but it is not going to be installed
 xubuntu-desktop : Depends: libpam-systemd but it is not going to be installed
                   Recommends: indicator-application but it is not going to be installed
                   Recommends: indicator-messages but it is not going to be installed
                   Recommends: xfce4-power-manager but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


seems that it's kidding with me :(

---

### Post by Bashing-om on 2015-01-21
tomschaack; Humm ..

I did have a typo in the "apt-cache depends  systemd-services" .. but, but ..

On my 14.04 system, I **DO NOT** have systemd installed, returns"
```

sysop@1404mini:~$ apt-cache depends systemd-services
systemd-services
  Depends: libacl1
  Depends: libc6
  Depends: libcap2
  Depends: libcgmanager0
  Depends: libdbus-1-3
  Depends: libnih-dbus1
  Depends: libnih1
  Depends: libselinux1
  Depends: libsystemd-daemon0
  Depends: libudev1
  Depends: udev
    udev:i386
  Depends: dbus
    dbus:i386
 |Depends: <systemd>
  Depends: systemd-shim
  Suggests: cgmanager
  Conflicts: <logind>
  Conflicts: <logind:i386>
  Breaks: <systemd>
  Breaks: <systemd:i386>
  Replaces: <logind>
    systemd-services:i386
    systemd-services
  Replaces: <logind:i386>
    systemd-services:i386
    systemd-services
  Replaces: <systemd>
  Replaces: <systemd:i386>
  Replaces: ubuntu-system-service
  Replaces: <ubuntu-system-service:i386>
  Conflicts: systemd-services:i386
sysop@1404mini:~$ apt-cache policy systemd
systemd:
  Installed: (none)
  Candidate: (none)
  Version table:
sysop@1404mini:~

```

So we are back to ' Depends: libpam-systemd but it is not going to be installed ' . Why ?
What returns:
```

apt-cache policy libpam-systemd

```
Should be:
> 
Package libpam-systemd

utopic-updates (admin): system and service manager - PAM module 
208-8ubuntu8.2: amd64 i386


Let's see where we go from here.

be advised: sometimes I wonder
[INDENT][INDENT]othertimes I do wonder
[/INDENT][/INDENT]

---

### Post by tomschaack on 2015-01-22
I finished by recovering config and data files and installed a fresh debian on it. Sick of ubuntu bugs.

Thx for your help anyway, but i guess this was a snake eating his tail...

---

### Post by Bashing-om on 2015-01-22
tomschaack; Ho Kay ....

That is one sure way of solving a problem.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

We will have a different adventure
[INDENT][INDENT][INDENT]some other time
[/INDENT][/INDENT][/INDENT]

---

