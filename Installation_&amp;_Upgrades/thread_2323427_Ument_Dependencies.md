---
title: "Ument Dependencies"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by Jay_Vala on 2016-05-05
Hello all

I have a problem which I am trying to solve from last 5 days. I am using Linux from 3 years and I was able to solve most issues that came me way but this thing is not easily going away. I tried every possible solution but stuck.

I am not a big fan of Libreoffice so I uninstalled it and installed Openoffice but that was too not that great. I thought I would have both and that's where the problem started, I was installing Libreoffice but it didnt install. So i thought I will remove Openoffice and install Libreoffice. But it says unmet dependencies which I tried solving with ```
sudo apt-get install -f
``` but I am getting this error

```

eading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  brasero-cdrkit hyphen-de hyphen-en-gb hyphen-en-us libaec0 libarmadillo6
  libarpack2 libblas-common libblas3 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libboost-iostreams1.58.0 libcdr-0.1-1
  libctemplate2v5 libdap17v5 libdapclient6v5 libepsilon1 libevent-2.0-5
  libfreehand-0.1-1 libfreexl1 libgeos-3.5.0 libgeos-c1v5 libgfortran3 libgif7
  libglc0 libgnome-2-0 libgnome2-0 libgnome2-bin libgnome2-common
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libgnomevfs2-0 libgnomevfs2-common libgtkmm-2.4-1v5 libhdf4-0-alt libhdf5-10
  libidl-2-0 libkeybinder0 libkmlbase1 libkmldom1 libkmlengine1 liblapack3
  libminizip1 libmspub-0.1-1 libnatpmp1 libnetcdf11 libodbc1 libogdi3.2
  libopenal-data libopenal1 libopenjp2-7 liborbit-2-0 liborbit2
  liborcus-0.10-0v5 libpagemaker-0.0-0 libpcrecpp0v5 libphysfs1 libpq5
  libproj9 libspatialite7 libsuperlu4 libsz2 libtinyxml2.6.2v5 liburiparser1
  libvisio-0.1-1 libvsqlitepp3v5 libvte-common libvte9 libxerces-c3.1 libzip4
  mysql-utilities mysql-workbench-data mythes-en-au mythes-en-us odbcinst
  odbcinst1debian2 openoffice.org-hyphenation proj-bin proj-data python-gconf
  python-gnome2 python-gobject python-keybinder python-mysql.connector
  python-notify python-pexpect python-ptyprocess python-pyodbc python-pyorbit
  python-pysqlite2 python-vte transmission-common warzone2100-data
  warzone2100-music
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-breeze libreoffice-style-hicontrast
  libreoffice-style-human libreoffice-style-oxygen libreoffice-style-sifr
  libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0 B/22,3 MB of archives.
After this operation, 84,7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 202323 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.1.2-0ubuntu1_all.deb ...
Unpacking libreoffice-common (1:5.1.2-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.1.2-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.2-9782
rmdir: failed to remove '/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/share/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
rmdir: failed to remove '/var/lib/libreoffice': No such file or directory
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2) ...
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.1.2-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by izznogooood on 2016-05-05
I see you have a lot of packages awaiting removal, any particular reason why you don't run "sudo apt autoremove"? It may seems you have some leftovers that very well may cause this.
If not try:
Have you tried to install "synaptic" and search for all packages named "openoficexxxx" and "libreofficexxxx". Mark the for removal (Purge). Then try reinstalling.

---

### Post by matt_symes on 2016-05-05
Hi

Do you have broken sources ?

Please post the output of these commands so someone can take a look.

```
cat /etc/lsb-release
```

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by izznogooood on 2016-05-05
Do this first! :)

> **matt_symes said:**
> Hi

Do you have broken sources ?

Please post the output of these commands so someone can take a look.

```
cat /etc/lsb-release
```

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

