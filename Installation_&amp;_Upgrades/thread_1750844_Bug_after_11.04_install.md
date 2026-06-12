---
title: "Bug after 11.04 install"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by FelipeAragao on 2011-05-05
Well, after some hard work, got to install ubuntu 11.04 and everything was fine.

Now I'm getting an error while trying to do anything with apt-get.

Here's the output:
```
felipe@felipe-Inspiron-N5010:~$ sudo apt-get -f install
[sudo] password for felipe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  liferea-data
The following NEW packages will be installed:
  liferea-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/385 kB of archives.
After this operation, 1,516 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 209712 files and directories currently installed.)
Unpacking liferea-data (from .../liferea-data_1.6.4-1ubuntu7_all.deb) ...
dpkg: error processing /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb (--unpack):
 trying to overwrite '/usr/share/liferea/pixmaps/available.png', which is also in package faenza-extras 0.9
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anyone knows how to solve it? I'm desperate.
Thanks in advance.

---

### Post by ReelExterminator on 2011-05-06
You can try removing the faenza-extras package to see if that fixes it. Google tells me it's a GNOME theme that replaces tray icons, including Liferea's, so maybe it's creating a conflict.

---

### Post by FelipeAragao on 2011-05-06
Hi. Thanks for the reply.

Don't know what to do exactly, so I tried this:
```
felipe@felipe-Inspiron-N5010:~$ sudo apt-get autoremove faenza-extras
[sudo] password for felipe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 liferea : Depends: liferea-data (= 1.6.4-1ubuntu7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
felipe@felipe-Inspiron-N5010:~$ sudo apt-get autoremove liferea-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package liferea-data is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 liferea : Depends: liferea-data (= 1.6.4-1ubuntu7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
felipe@felipe-Inspiron-N5010:~$ sudo apt-get install liferea-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  liferea-data
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/385 kB of archives.
After this operation, 1,516 kB of additional disk space will be used.
(Reading database ... 209712 files and directories currently installed.)
Unpacking liferea-data (from .../liferea-data_1.6.4-1ubuntu7_all.deb) ...
dpkg: error processing /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb (--unpack):
 trying to overwrite '/usr/share/liferea/pixmaps/available.png', which is also in package faenza-extras 0.9
Processing triggers for hicolor-icon-theme ...
^[[AErrors were encountered while processing:
 /var/cache/apt/archives/liferea-data_1.6.4-1ubuntu7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Didn't Work. :(

---

### Post by ReelExterminator on 2011-05-06
Maybe try
```
sudo apt-get remove faenza-extras
```
I am not sure why 'autoremove' didn't work. Hope that helps!

---

### Post by FelipeAragao on 2011-05-07
Thanks for the reply!

Looks like that doesn't work as well.
```
felipe@felipe-Inspiron-N5010:~$ sudo apt-get remove faenza-extras
[sudo] password for felipe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 liferea : Depends: liferea-data (= 1.6.4-1ubuntu7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by ReelExterminator on 2011-05-08
Darn. I don't know where to go from here. Hopefully someone else can chime in.

---

