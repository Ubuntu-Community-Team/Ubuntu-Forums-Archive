---
title: "can not install and upgrade, unmet dependencies"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by pregnanter on 2011-05-29
&#9492;&#9472;&#9596; $ sudo apt-get upgrade 
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
gnome-shell : Depends: gnome-themes-standard (>= 2.91) but it is not installed
E: Unmet dependencies. Try using -f.

------------------------------

&#9492;&#9472;&#9596; $ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
gnome-themes-standard
The following NEW packages will be installed:
gnome-themes-standard
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 980 kB of archives.
After this operation, 6,226 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/ricotz/testing/ubuntu/](http://ppa.launchpad.net/ricotz/testing/ubuntu/) natty/main gnome-themes-standard i386 3.1.1-0ubuntu1~11.10~ricotz0 [980 kB]
Fetched 980 kB in 3min 9s (5,183 B/s) 
(Reading database ... 
dpkg: warning: files list file for package `gnome-themes-ubuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-themes-selected' missing, assuming package has no files currently installed.
(Reading database ... 338597 files and directories currently installed.)
Unpacking gnome-themes-standard (from .../gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb (--unpack):
trying to overwrite '/usr/share/icons/HighContrastInverse/index.theme', which is also in package gnome-accessibility-themes 3.0.0-0ubuntu1~build2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/gnome-themes-standard_3.1.1-0ubuntu1~11.10~ricotz0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


* so that I can not install any softwares now . damn it.

---

### Post by zvacet on 2011-05-30
```
sudo dpkg --configure -a
```

---

### Post by Fajner1 on 2011-06-05
I have the exact same problem, and 

```
sudo dpkg --configure -a
```returns

```
dpkg: dependency problems prevent configuration of gnome-shell:
 gnome-shell depends on gnome-themes-standard (>= 2.91); however:
  Package gnome-themes-standard is not installed.
dpkg: error processing gnome-shell (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-shell
```



---

Also, should I start a new thread, or can I post on this one because I have the exact same problem?

---

### Post by Fajner1 on 2011-06-05
I found a solution. I used Synaptic and it let me remove gnome-shell. I honestly don't know why i didn't think of it before...

---

