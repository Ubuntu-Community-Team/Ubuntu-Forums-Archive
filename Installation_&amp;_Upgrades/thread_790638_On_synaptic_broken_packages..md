---
title: "On synaptic broken packages."
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by delilahjed44 on 2008-05-11
Hey everyone..
     Synaptic is telling me I have broken packages and unmet dependencies, so I located the packages and tried to do sudo apt-get -f install..here is what I am receiving back

This first one is from synaptic:
- E: /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb: trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu


acroread (version 8.1.2-0medibuntu1) will be installed
acroread-escript (version 8.1.2-0medibuntu1) will be re-installed
acroread-plugins (version 8.1.2-0medibuntu1) will be re-installed


Here is what I am getting from the terminal with sudo apt-get -f-install
-Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0 libxine1-gnome python-wxversion python-wxgtk2.6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  acroread
The following NEW packages will be installed:
  acroread
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
2 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 73.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 109529 files and directories currently installed.)
Unpacking acroread (from .../acroread_8.1.2-0medibuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/bin/acroread', which is also in package adobereader-enu
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_8.1.2-0medibuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returne


I have not a clue how to correct this issue..and my system seems to be running fine so I dont know whats up here..

Sherri

Something else I noticed..where my name is in here it says I only thank o times and thanked 1 time in one post..not sure what that applies because I am always saying thank you and I am appreciative of the open scource..so as I said dont know what thats all about...

Sherri

---

### Post by bapoumba on 2008-05-11
Please try to remove adobereader-enu and then run:
```
sudo apt-get install -f
```
[http://ubuntuforums.org/showthread.php?t=721017]("http://ubuntuforums.org/showthread.php?t=721017")

The thank yous your profile is talking about is a [forums feature]("http://ubuntuforums.org/showthread.php?t=702596"). You can thank someone by clicking on the small blue ribbon icon bottom right of each post. You can also be thanked. [More about forums features]("http://ubuntuforums.org/showthread.php?t=726219").

---

### Post by delilahjed44 on 2008-05-11
Hey let me ask you this..will this un-install any reader I have with Adobe..as I have some things that require it..just did not know..but if its wrecking the system its best to get it off anyhow..

Sherri
 Thank you tons

---

### Post by delilahjed44 on 2008-05-11
> **bapoumba said:**
> Please try to remove adobereader-enu and then run:
```
sudo apt-get install -f
```
[http://ubuntuforums.org/showthread.php?t=721017]("http://ubuntuforums.org/showthread.php?t=721017")

The thank yous your profile is talking about is a [forums feature]("http://ubuntuforums.org/showthread.php?t=702596"). You can thank someone by clicking on the small blue ribbon icon bottom right of each post. You can also be thanked. [More about forums features]("http://ubuntuforums.org/showthread.php?t=726219").
 

 Hey bapumba,,problem fixed..big thank you on this..

 Sherri

---

### Post by bapoumba on 2008-05-12
You're welcome, glad to see you got it to work :)

---

