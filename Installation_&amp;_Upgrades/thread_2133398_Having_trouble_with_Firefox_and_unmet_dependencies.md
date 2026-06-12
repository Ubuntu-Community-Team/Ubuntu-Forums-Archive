---
title: "Having trouble with Firefox and unmet dependencies"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by sydewayzlocc on 2013-04-08
secretfire@secretfire-desktop:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts firefox-gnome-support
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 388 not upgraded.
3 not fully installed or removed.
Need to get 0 B/24.8 MB of archives.
After this operation, 55.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 155835 files and directories currently installed.)
Unpacking firefox (from .../firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/applications/firefox.desktop', which is also in package kubuntu-firefox-installer 12.04ubuntu1
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help!!

---

### Post by zhelto on 2013-04-08
I had the same problem today just after installation kubuntu 12.10 amd64.
The solving is rather easy.
I delete pakages
1) firefox-globalmenu
2) kubuntu-firefox-installer
in default package manager (Muon).
After it 
$sudo apt-get upgrade
And it works as usuall.

P.S. Then i upgrade pakages from default update manager (Muon), reboot system, install synaptic
$ sudo apt-get install synaptic
and install firefox with synaptic.

P.P.S. Maybe some of my steps not necessary, but i hope my description will help somebody.

---

