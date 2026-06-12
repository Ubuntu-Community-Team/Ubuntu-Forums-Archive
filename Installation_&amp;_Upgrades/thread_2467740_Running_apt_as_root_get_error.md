---
title: "Running apt as root get error"
date: 2021-10-06
forum: Installation &amp; Upgrades
---

### Post by greene-dog on 2021-10-06
Trying to run "apt upgrade" as root and it give me error and permission issues

As root what is happening and where are permission that don't allow root to do anything?

As root I run apt upgrade and get the following





root@odroid-nas:~# apt upgrade

Reading package lists... Done

Building dependency tree

Reading state information... Done

You might want to run 'apt --fix-broken install' to correct these.

The following packages have unmet dependencies:

 libnss-systemd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

 libpam-systemd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

 systemd : Depends: libsystemd0 (= 245.4-4ubuntu3.11) but 245.4-4ubuntu3.13 is installed

 systemd-sysv : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

 systemd-timesyncd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by deadflowr on 2021-10-06
What permission issues?
The only issue I see is that the package listing of available updates are out of date, or out of whack.

Run
```
apt update
apt upgrade
```
if still issues 
try with
```
apt full-upgrade
```
if still issues, post back what the results are.

---

### Post by TheFu on 2021-10-06
```
You might want to run 'apt --fix-broken install' to correct these.
```
is the output of the command.  Did you try that?

Dependency issues ARE NOT the same as permissions issues.  Is there plenty of storage in the correct places to allow the prior upgrades to happen?  People often miss that the OS partition is full, but their /home partition has plenty of space.

---

### Post by greene-dog on 2021-10-06
I found this

in  /etc/apt/sources.list.d/pms.list was

#deb [https://dev2day.de/pms/](https://dev2day.de/pms/) jessie main
deb [https://dev2day.de/pms/](https://dev2day.de/pms/) stretch main

I added # to the second one and the issue went away and got this

Do you want to continue? [Y/n]
(Reading database ... 60088 files and directories currently installed.)
Preparing to unpack .../systemd_245.4-4ubuntu3.13_armhf.deb ...
Unpacking systemd (245.4-4ubuntu3.13) over (245.4-4ubuntu3.11) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb (--unpack):
 unable to create '/usr/bin/bootctl.dpkg-new' (while processing './usr/bin/bootctl'): Operation not permitted
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by greene-dog on 2021-10-06
I just tried this

root@odroid-nas:~# apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnss-systemd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed
 libpam-systemd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed
 systemd : Depends: libsystemd0 (= 245.4-4ubuntu3.11) but 245.4-4ubuntu3.13 is installed
 systemd-sysv : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed
 systemd-timesyncd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by greene-dog on 2021-10-06
tried this

root@odroid-nas:~# apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  systemd
Suggested packages:
  systemd-container
The following packages will be upgraded:
  systemd
1 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
5 not fully installed or removed.
Need to get 0 B/3651 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
(Reading database ... 60088 files and directories currently installed.)
Preparing to unpack .../systemd_245.4-4ubuntu3.13_armhf.deb ...
Unpacking systemd (245.4-4ubuntu3.13) over (245.4-4ubuntu3.11) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb (--unpack):
 unable to create '/usr/bin/bootctl.dpkg-new' (while processing './usr/bin/bootctl'): Operation not permitted
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by TheFu on 2021-10-06
If you change any repos, **sudo apt update** is required before running any other command. If you did that already, then ... 

It would be a good idea to remove any packages that were installed with either jessie or stretch repos.  Those aren't from Canonical.  Ubuntu software and Debian software isn't always compatible. There are different dependencies and getting into "apt hell" is likely when leaving the Canonical repo farm.

**sudo aptitude **
will provide different resolutions to apt dependency issues.  If you don't like the first one, say no and another should be offered.  Don't like that one?  Say no and another should be offered.  Eventually, you may see the solution that removes those Debian repo packages ...

If not, if it were me, I'd pave the system (nuke it from orbit), learn a lesson, and do a fresh install followed by restoring all my data, settings, and packages that don't use outside repos.  Of course, this requires having backups.

The best way to avoid APT hell (or RPM hell) is not to do things that get you into it.
[LIST]
[*]Don't use sources from outside the Canonical repos.
[*]Don't download and install .deb files directly.
[*]Do patch every week and fix any tiny issue with that process ASAP.  Like a tiny leak in a roof, APT issues seldom get better over time.
[*]Never attemp a migration to a new release if your system isn't fully patched and fully supported (the current and target releases). This will never fix issue.
[*]Do have backups, at least weekly, which can be used to avoid these sorts of issues.
[*]Do check the log files for issues at least weekly, if not daily.  I use **logwatch** to filter all the junk so only about 20 lines per system need to be reviewed.  Logwatch emails me the items in the system logs that are odd daily, so I don't really get to forget it.
[/LIST]

If I've spent more than 45 minutes trying to solve an issue like this, that is the time it takes me to restore onto a fresh install everything that makes a systems "my system", so I stop working the issue and just nuke it from orbit. The 2nd time around, because whatever I did was less than a week ago, I should know what caused the APT issue and be able to avoid it.

YMMV.

Did you check the disk storage available?

---

### Post by greene-dog on 2021-10-07
I meant to add this in my first post... added info.. some might be the same info


As root I run apt upgrade and get the following





root@odroid-nas:~# apt upgrade

Reading package lists... Done

Building dependency tree

Reading state information... Done

You might want to run 'apt --fix-broken install' to correct these.

The following packages have unmet dependencies:

 libnss-systemd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

 libpam-systemd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

 systemd : Depends: libsystemd0 (= 245.4-4ubuntu3.11) but 245.4-4ubuntu3.13 is installed

 systemd-sysv : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

 systemd-timesyncd : Depends: systemd (= 245.4-4ubuntu3.13) but 245.4-4ubuntu3.11 is installed

E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).









Then I run apt --fix-broken install get the following



root@odroid-nas:~# apt --fix-broken install

Reading package lists... Done

Building dependency tree

Reading state information... Done

Correcting dependencies... Done

The following additional packages will be installed:

  systemd

Suggested packages:

  systemd-container

The following packages will be upgraded:

  systemd

1 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.

5 not fully installed or removed.

Need to get 0 B/3651 kB of archives.

After this operation, 0 B of additional disk space will be used.

Do you want to continue? [Y/n]

(Reading database ... 60088 files and directories currently installed.)

Preparing to unpack .../systemd_245.4-4ubuntu3.13_armhf.deb ...

Unpacking systemd (245.4-4ubuntu3.13) over (245.4-4ubuntu3.11) ...

dpkg: error processing archive /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb (--unpack):

 unable to create '/usr/bin/bootctl.dpkg-new' (while processing './usr/bin/bootctl'): Operation not permitted

dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)

Errors were encountered while processing:

 /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by greene-dog on 2021-10-07
I ran history on root and got this for what I installed when I built it



************************

root@odroid-nas:~# cat history.txt
    1  history
    2  apt-get update
    3  apt-get upgrade
    4  ip addr show
    5  date
    6  time
    7  name
    8  l;kfjasifj
    9  google
   10  apt-get install libexpat1 -y
   11  wget -O - [https://dev2day.de/pms/dev2day-pms.gpg.key](https://dev2day.de/pms/dev2day-pms.gpg.key) | sudo apt-key add -
   12  echo "deb [https://dev2day.de/pms/](https://dev2day.de/pms/) jessie main" | sudo tee /etc/apt/sources.list.d/pms.list
   13  spt-get update
   14  apt-get update
   15  apt-get install plexmediaserver -y
   16  apt-get update
   17  apt-get install plexmediaserver -y
   18  apt-get update
   19  apt-get update && apt-get upgrade
   20  vi /etc/apt/sources.list
   21  vi /etc/apt/sources.list.d/odroid.list
   22  vi /etc/apt/sources.list.d/odroid.list.distUpgrade
   23  vi /etc/apt/sources.list.d/odroid.list.save
   24  grep dev2day /etc/apt/sources.list.d/*
   25  vi /etc/apt/sources.list.d/pms.list
   26  apt-get update
   27  apt-get upgrade
   28  pwd
   29  wget -O - [https://dev2day.de/pms/dev2day-pms.gpg.key](https://dev2day.de/pms/dev2day-pms.gpg.key) | apt-key add -
   30  apt-get install plexmediaserver-installer
   31  wget [https://downloads.plex.tv/plex-media-server-new/1.19.3.2852-219a9974e/](https://downloads.plex.tv/plex-media-server-new/1.19.3.2852-219a9974e/)
   32  wget [https://downloads.plex.tv/plex-media-server-new/1.19.3.2852-219a9974e/debian/plexmediaserver_1.19.3.2852-219a9974e_amd64.deb](https://downloads.plex.tv/plex-media-server-new/1.19.3.2852-219a9974e/debian/plexmediaserver_1.19.3.2852-219a9974e_amd64.deb)
   33  dpkg &#8211;i plexmediaserver_1.19.3..2852-219a9974e_amd64.debcat /ert
   34  cat /etc/*-release
   35  clera
   36  clear
   37  cat /etc/*-release
   38  pwd
   39  ll
   40  dpk -i plexmediaserver_1.19.3.2852-219a9974e_amd64.deb
   41  dpkg -i plexmediaserver_1.19.3.2852-219a9974e_amd64.deb
   42  wget [https://downloads.plex.tv/plex-media-server-new/1.22.0.4163-d8c4875dd/debian/plexmediaserver_1.22.0.4163-d8c4875dd_armhf.deb](https://downloads.plex.tv/plex-media-server-new/1.22.0.4163-d8c4875dd/debian/plexmediaserver_1.22.0.4163-d8c4875dd_armhf.deb)
   43  wget [https://downloads.plex.tv/plex-media-server-new/1.22.0.4163-d8c4875dd/debian/plexmediaserver_1.22.0.4163-d8c4875dd_arm64.deb](https://downloads.plex.tv/plex-media-server-new/1.22.0.4163-d8c4875dd/debian/plexmediaserver_1.22.0.4163-d8c4875dd_arm64.deb)
   44  dpkg -i plexmediaserver_1.22.0.4163-d8c4875dd_armhf.deb
   45  systemctl status plexmediaserver
   46  systemctl start  plexmediaserver


**********************

---

### Post by greene-dog on 2021-10-07
update...

I did the following and got the same.... see bottom lines

Deleted the archive .deb files in  /var/cache/apt/archives

root@odroid-nas:/var/cache/apt/archives# rm systemd-sysv_245.4-4ubuntu3.13_armhf.deb
root@odroid-nas:/var/cache/apt/archives# apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  systemd
Suggested packages:
  systemd-container
The following packages will be upgraded:
  systemd
1 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
5 not fully installed or removed.
Need to get 0 B/3651 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
(Reading database ... 57582 files and directories currently installed.)
Preparing to unpack .../systemd_245.4-4ubuntu3.13_armhf.deb ...
Unpacking systemd (245.4-4ubuntu3.13) over (245.4-4ubuntu3.11) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb (--unpack):
 unable to create '/usr/bin/bootctl.dpkg-new' (while processing './usr/bin/bootctl'): Operation not permitted
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@odroid-nas:/var/cache/apt/archives# rm *.deb
root@odroid-nas:/var/cache/apt/archives# apt update
Hit:1 [http://deb.odroid.in/5422-s](http://deb.odroid.in/5422-s) focal InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal InRelease
Get:3 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-updates InRelease [114 kB]
Hit:4 [http://ppa.launchpad.net/hardkernel/ppa/ubuntu](http://ppa.launchpad.net/hardkernel/ppa/ubuntu) focal InRelease
Get:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-backports InRelease [101 kB]
Get:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-security InRelease [114 kB]
Get:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-updates/main armhf Packages [826 kB]
Get:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-updates/universe armhf Packages [706 kB]
Fetched 1860 kB in 6s (308 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
46 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@odroid-nas:/var/cache/apt/archives# apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  systemd
Suggested packages:
  systemd-container
The following packages will be upgraded:
  systemd
1 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
5 not fully installed or removed.
Need to get 3651 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
Get:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-updates/main armhf systemd armhf 245.4-4ubuntu3.13 [3651 kB]
Fetched 3651 kB in 2s (2069 kB/s)
(Reading database ... 57582 files and directories currently installed.)
Preparing to unpack .../systemd_245.4-4ubuntu3.13_armhf.deb ...
Unpacking systemd (245.4-4ubuntu3.13) over (245.4-4ubuntu3.11) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb (--unpack):
 unable to create '/usr/bin/bootctl.dpkg-new' (while processing './usr/bin/bootctl'): Operation not permitted
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_245.4-4ubuntu3.13_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@odroid-nas:/var/cache/apt/archives#

---

### Post by TheFu on 2021-10-08
> **TheFu said:**
> 
Did you check the disk storage available?

?

---

### Post by greene-dog on 2021-10-08
ok... we can stop thinking about this and trying to figure it out.

I just rebuilt the system and it is up and running.

Thanks for all the help!

---

### Post by ajgreeny on 2021-10-08
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

