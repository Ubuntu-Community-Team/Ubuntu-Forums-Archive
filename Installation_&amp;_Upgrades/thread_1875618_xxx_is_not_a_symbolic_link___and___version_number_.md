---
title: "xxx is not a symbolic link   and   version number invalid"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-11-05
Recently I get every time I install something a couple of other errors/warnings. Can somebody help me to fix that, please:



> sudo apt-get install qtnx
[sudo] password for ronald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-sil-gentium libreoffice-report-builder-bin ttf-sil-gentium-basic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnxcl1 libxcomp3 nxproxy
Suggested packages:
  x2goclient
The following NEW packages will be installed:
  libnxcl1 libxcomp3 nxproxy qtnx
0 upgraded, 4 newly installed, 0 to remove and 93 not upgraded.
Need to get 480 kB of archives.
After this operation, 1,479 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) oneiric/universe libxcomp3 amd64 3.5.0-1-0ubuntu1 [342 kB]
Get:2 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) oneiric/universe nxproxy amd64 3.5.0-1-0ubuntu1 [5,788 B]
Get:3 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) oneiric/universe libnxcl1 amd64 0.9-3ubuntu1 [45.0 kB]
Get:4 [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) oneiric/universe qtnx amd64 0.9-3ubuntu4 [87.4 kB]
Fetched 480 kB in 2s (229 kB/s)
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20523 package 'virtualbox':
 error in Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20524 package 'virtualbox':
 error in Config-Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 33425 package 'ffmpeg':
 error in Version string '5:git-f4f4e12-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 79647 package 'twittenator':
 error in Version string 'v1.24': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 87910 package 'qt-faststart':
 error in Version string 'git-f4f4e12-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 88074 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 88075 package 'virtualbox-3.1':
 error in Config-Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 91336 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 91337 package 'virtualbox-2.1':
 error in Config-Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 22487 package 'virtualbox':
 error in Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 36726 package 'ffmpeg':
 error in Version string '5:git-f4f4e12-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 88057 package 'twittenator':
 error in Version string 'v1.24': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 97344 package 'qt-faststart':
 error in Version string 'git-f4f4e12-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 97445 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 100870 package 'virtualbox-2.2':
 error in Version string '2.2.4-47978_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 101025 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
Selecting previously deselected package libxcomp3.
(Reading database ... 403400 files and directories currently installed.)
Unpacking libxcomp3 (from .../libxcomp3_3.5.0-1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package nxproxy.
Unpacking nxproxy (from .../nxproxy_3.5.0-1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libnxcl1.
Unpacking libnxcl1 (from .../libnxcl1_0.9-3ubuntu1_amd64.deb) ...
Selecting previously deselected package qtnx.
Unpacking qtnx (from .../qtnx_0.9-3ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for menu ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 20523 package 'virtualbox':
 error in Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 20524 package 'virtualbox':
 error in Config-Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 33425 package 'ffmpeg':
 error in Version string '5:git-f4f4e12-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 79647 package 'twittenator':
 error in Version string 'v1.24': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 87910 package 'qt-faststart':
 error in Version string 'git-f4f4e12-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 88074 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 88075 package 'virtualbox-3.1':
 error in Config-Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 91336 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 91337 package 'virtualbox-2.1':
 error in Config-Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20523 package 'virtualbox':
 error in Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 20524 package 'virtualbox':
 error in Config-Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 33441 package 'ffmpeg':
 error in Version string '5:git-f4f4e12-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 79695 package 'twittenator':
 error in Version string 'v1.24': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 87958 package 'qt-faststart':
 error in Version string 'git-f4f4e12-1': version number does not start with digit
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 88122 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 88123 package 'virtualbox-3.1':
 error in Config-Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 91384 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 91385 package 'virtualbox-2.1':
 error in Config-Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
Setting up libxcomp3 (3.5.0-1-0ubuntu1) ...
Setting up nxproxy (3.5.0-1-0ubuntu1) ...
Setting up libnxcl1 (0.9-3ubuntu1) ...
Setting up qtnx (0.9-3ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libppsvodres.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsvodnet.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppssg.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsfds.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsapi.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsbase.so.0 is not a symbolic link

Processing triggers for menu ...
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 20523 package 'virtualbox':
 error in Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 20524 package 'virtualbox':
 error in Config-Version string '1.5.6-28266_Ubuntu_gutsy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 33441 package 'ffmpeg':
 error in Version string '5:git-f4f4e12-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 79695 package 'twittenator':
 error in Version string 'v1.24': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 87958 package 'qt-faststart':
 error in Version string 'git-f4f4e12-1': version number does not start with digit
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 88122 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 88123 package 'virtualbox-3.1':
 error in Config-Version string '3.1.4-57640_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 91384 package 'virtualbox-2.1':
 error in Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number
dpkg-query: warning: parsing file '/var/lib/dpkg/status' near line 91385 package 'virtualbox-2.1':
 error in Config-Version string '2.1.4-42893_Ubuntu_hardy': invalid character in revision number


---

