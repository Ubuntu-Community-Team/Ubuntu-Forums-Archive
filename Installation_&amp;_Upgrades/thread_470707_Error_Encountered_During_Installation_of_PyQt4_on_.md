---
title: "Error Encountered During Installation of PyQt4 on Ubuntu 7.04"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by freiubtheit on 2007-06-11
The following error messages were received during the installtion of PyQt4:

"root@XXXX:~# apt-get install pyqt4*
Reading package lists... Done
Building dependency tree... Done
Note, selecting memaid-pyqt for regex 'pyqt4*'
Note, selecting pyqt-tools for regex 'pyqt4*'
Note, selecting pyqt4-dev-tools for regex 'pyqt4*'
The following extra packages will be installed:
  memaid-pyqt pyqt4-dev-tools python-qt4
Suggested packages:
  python-qt4-dbg
Recommended packages:
  python-elementtree
The following NEW packages will be installed:
  memaid-pyqt pyqt4-dev-tools python-qt4
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 3794kB of archives.
After unpacking 17.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) feisty/universe memaid-pyqt 0.2.5-2build1 [137kB]
Get:2 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) feisty/main python-qt4 4.1-0ubuntu6 [3535kB]
Get:3 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) feisty/universe pyqt4-dev-tools 4.1-0ubuntu6 [122kB]
Fetched 3794kB in 44s (84.7kB/s)                                               
Selecting previously deselected package memaid-pyqt.
(Reading database ... 239945 files and directories currently installed.)
Unpacking memaid-pyqt (from .../memaid-pyqt_0.2.5-2build1_i386.deb) ...
Selecting previously deselected package python-qt4.
Unpacking python-qt4 (from .../python-qt4_4.1-0ubuntu6_i386.deb) ...
Selecting previously deselected package pyqt4-dev-tools.
Unpacking pyqt4-dev-tools (from .../pyqt4-dev-tools_4.1-0ubuntu6_i386.deb) ...
[B]Setting up newpki-server (2.0.0+rc1-8) ...
Starting NewPKI: newpki-serverinvoke-rc.d: initscript newpki-server, action "start" failed.
dpkg: error processing newpki-server (--configure):
 subprocess post-installation script returned error exit status 1[/B]
[B]Setting up iiimf-htt-server (11.4.1870-7.3build1) ...
Starting Internet/Intranet Input Method server: htt_serverinvoke-rc.d: initscript iiimf-htt-server, action "start" failed.
dpkg: error processing iiimf-htt-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of iiimf-htt-le-newpy:
 iiimf-htt-le-newpy depends on iiimf-htt-server; however:
  Package iiimf-htt-server is not configured yet.
dpkg: error processing iiimf-htt-le-newpy (--configure):
 dependency problems - leaving unconfigured[/B]
Setting up memaid-pyqt (0.2.5-2build1) ...

Setting up python-qt4 (4.1-0ubuntu6) ...

Setting up pyqt4-dev-tools (4.1-0ubuntu6) ...
[B]Errors were encountered while processing:
 newpki-server
 iiimf-htt-server
 iiimf-htt-le-newpy
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]"

Any pointer?

---

