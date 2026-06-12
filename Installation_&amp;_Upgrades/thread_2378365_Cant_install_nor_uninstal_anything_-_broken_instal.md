---
title: "Cant install nor uninstal anything - broken instal-info"
date: 2017-11-22
forum: Installation &amp; Upgrades
---

### Post by earosselot on 2017-11-22
hi. im using ubuntu 16.04, recently i tried to install a new version of QGIS (qgis.org), but, i dont uninstall the previous version (newby). That was the begining of my problems, now i cant install nor uninstall neither of the versions. Before post here i have been hours reading forums and triyng to solve it, but nothing seems to work, some help could be awesome !

I will paste the console errors here:

```
eduardo@eduardo-system:~$ sudo apt-get install qgis
[sudo] password for eduardo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 qgis : Depends: libqgis-analysis2.18.14 but it is not going to be installed
        Depends: libqgis-app2.18.14 but it is not going to be installed
        Depends: libqgis-core2.18.14 but it is not going to be installed
        Depends: libqgis-gui2.18.14 but it is not going to be installed
        Depends: libqgis-networkanalysis2.18.14 but it is not going to be installed
        Depends: python-qgis (= 1:2.18.14+24xenial) but 1:2.18.13+24xenial is to be installed
        Depends: qgis-providers (= 1:2.18.14+24xenial) but 1:2.18.13+24xenial is to be installed
        Depends: qgis-common (= 1:2.18.14+24xenial) but 1:2.18.13+24xenial is to be installed
 qgis-plugin-grass : Depends: qgis (= 1:2.18.13+24xenial) but 1:2.18.14+24xenial is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
eduardo@eduardo-system:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libqgis-analysis2.18.13 libqgis-app2.18.13 libqgis-core2.18.13 libqgis-gui2.18.13 libqgis-networkanalysis2.18.13 libqgis-server2.18.13 libqgisgrass7-2.18.13
  libqgispython2.18.13
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libqgis-analysis2.18.14 libqgis-app2.18.14 libqgis-core2.18.14 libqgis-customwidgets libqgis-gui2.18.14 libqgis-networkanalysis2.18.14 libqgis-server2.18.14
  libqgisgrass7-2.18.14 libqgispython2.18.14 python-qgis python-qgis-common qgis qgis-common qgis-plugin-grass qgis-plugin-grass-common qgis-provider-grass qgis-providers
  qgis-providers-common
Suggested packages:
  gpsbabel
The following NEW packages will be installed:
  libqgis-analysis2.18.14 libqgis-app2.18.14 libqgis-core2.18.14 libqgis-gui2.18.14 libqgis-networkanalysis2.18.14 libqgis-server2.18.14 libqgisgrass7-2.18.14
  libqgispython2.18.14 qgis
The following packages will be upgraded:
  libqgis-customwidgets python-qgis python-qgis-common qgis-common qgis-plugin-grass qgis-plugin-grass-common qgis-provider-grass qgis-providers qgis-providers-common
9 upgraded, 9 newly installed, 0 to remove and 100 not upgraded.
1 not fully installed or removed.
Need to get 0 B/60,7 MB of archives.
After this operation, 59,9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up install-info (6.1.0.dfsg.1-5) ...
/usr/sbin/update-info-dir: 2: /etc/environment: Acquire::http:Proxy: not found
dpkg: error processing package install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i hope someone can help me, thanks !!

---

