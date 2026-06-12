---
title: "Dependency kerfuffle with upgrade to 20.04; Please kindly advise"
date: 2020-07-17
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2020-07-17
So bit of a conundrum/rubik cube/catch 22/maze situation


Got there from 18.04 through 19.10 >>


```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
```


but quite a few dependencies moaning:  [forgot to say when upgrading to 20.04 it only went 10% in then some kink appeared reloaded with fingers crossed]




```
 /var/cache/apt/libglx-dev/archives/_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libgl-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libegl-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libgles-dev_1.3.1-1_amd64.deb

``` 
 

 Most things "work" but I would like a clean system

I did a few things as can be seen below but caught in a maze so not sure how to proceed
PS   also used sudo synaptic Broken Packages and similar results
 
 #############################
 
 
```
** sudo apt-get install -f**
[sudo] password for shan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gmt-dcw gmt-gshhg-high libxmlsec1 libxmlsec1-nss
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  grass-core jackd2 jackd2-firewire libalgorithms1 libcoin80c libdxflib3
  libegl-dev libgdal-grass libgl-dev libgles-dev libglx-dev libimageclasses1
  liblaszip8 libmapcache1 libopenscenegraph160 libopenthreads21 libosgearth5
  libosgearthannotation5 libosgearthfeatures5 libosgearthsymbology5
  libosgearthutil5 libpdal-base9 libpdal-plugin-faux libpdal-plugin-icebridge
  libpdal-plugin-pgpointcloud libpdal-plugin-python libpdal-plugin-sqlite
  libpdal-plugins libpdal-util9 libpq-dev libpq5 libqgisgrass7-3.10.4
  libvigraimpex11 mapcache-tools openscenegraph osgearth pdal pktools postgis
  postgresql-12 postgresql-12-postgis-3 postgresql-12-postgis-3-scripts
  postgresql-client-12 qgis-provider-grass qjackctl saga saga-common sysstat
Suggested packages:
  grass-dev gnuplot gpsbabel gpstrans python3-rpy2 python3-termcolor
  jack-tools libopenal0a libsimage-dev postgresql-doc-12 osgearth-data
  pdal-doc postgis-gui isag
The following packages will be REMOVED
  appmenu-qt carla-git carla-lv2 carla-vst gmt libdbusmenu-qt2 libgmt5
  libopencv-calib3d3.2 libopencv-features2d3.2 libopencv-highgui3.2
  libopencv-imgcodecs3.2 libopencv-videoio3.2 libopenscenegraph-3.4-131
  libopenscenegraph100v5 libpdal-base8 libpdal-plugin-greyhound
  libqgis-3d3.4.10 libqgis-analysis3.4.10 libqgis-app3.4.10 libqgis-core3.4.10
  libqgis-gui3.4.10 libqgis-server3.4.10 libqgisgrass7-3.4.10
  libqgispython3.4.10 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-dev libqt4-dev-bin libqt4-help libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqtassistantclient4 libqtdbus4 libqtgui4 postgresql-11-postgis-2.5
  pprepair puddletag python-qt4 qdbus qt-at-spi qt4-linguist-tools
The following NEW packages will be installed
  jackd2 jackd2-firewire libegl-dev libgl-dev libgles-dev libglx-dev
  libopenscenegraph160 libopenthreads21 libpdal-base9 libpdal-util9
  libqgisgrass7-3.10.4 libvigraimpex11 postgresql-12 postgresql-12-postgis-3
  postgresql-12-postgis-3-scripts postgresql-client-12 qjackctl sysstat
The following packages will be upgraded:
  grass-core libalgorithms1 libcoin80c libdxflib3 libgdal-grass
  libimageclasses1 liblaszip8 libmapcache1 libosgearth5 libosgearthannotation5
  libosgearthfeatures5 libosgearthsymbology5 libosgearthutil5
  libpdal-plugin-faux libpdal-plugin-icebridge libpdal-plugin-pgpointcloud
  libpdal-plugin-python libpdal-plugin-sqlite libpdal-plugins libpq-dev libpq5
  mapcache-tools openscenegraph osgearth pdal pktools postgis
  qgis-provider-grass saga saga-common
30 to upgrade, 18 to newly install, 51 to remove and 2020 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/51.2 MB of archives.
After this operation, 250 MB disk space will be freed.
Do you want to continue? [Y/n] y
Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: files list file for package 'libgtk1.2-doc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk1.2-dbg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk1.2-common' missing; assuming package has no files currently installed
(Reading database ... 413626 files and directories currently installed.)
Preparing to unpack .../libglx-dev_1.3.1-1_amd64.deb ...
Unpacking libglx-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libglx-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/GL/glx.h', which is also in package mesa-common-dev:amd64 20.0.8-0ubuntu1~18.04.1
Preparing to unpack .../libgl-dev_1.3.1-1_amd64.deb ...
Unpacking libgl-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libgl-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/GL/gl.h', which is also in package mesa-common-dev:amd64 20.0.8-0ubuntu1~18.04.1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../libegl-dev_1.3.1-1_amd64.deb ...
Unpacking libegl-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libegl-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/EGL/egl.h', which is also in package libegl1-mesa-dev:amd64 20.0.8-0ubuntu1~18.04.1
Preparing to unpack .../libgles-dev_1.3.1-1_amd64.deb ...
Unpacking libgles-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libgles-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/GLES2/gl2.h', which is also in package libgles2-mesa-dev:amd64 20.0.8-0ubuntu1~18.04.1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libglx-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libgl-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libegl-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libgles-dev_1.3.1-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)





```

========================


```
**sudo aptitude**
Performing actions...
Extract templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: files list file for package 'libgtk1.2-doc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk1.2-dbg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk1.2-common' missing; assuming package has no files currently installed
(Reading database ... 413626 files and directories currently installed.)
Preparing to unpack .../libglx-dev_1.3.1-1_amd64.deb ...
Unpacking libglx-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libglx-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/GL/glx.h', which is also in package mesa-common-dev:amd64 20.0.8-0ubuntu1~18.04.1
Preparing to unpack .../libgl-dev_1.3.1-1_amd64.deb ...
Unpacking libgl-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libgl-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/GL/gl.h', which is also in package mesa-common-dev:amd64 20.0.8-0ubuntu1~18.04.1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../libegl-dev_1.3.1-1_amd64.deb ...
Unpacking libegl-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libegl-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/EGL/egl.h', which is also in package libegl1-mesa-dev:amd64 20.0.8-0ubuntu1~18.04.1
Preparing to unpack .../libgles-dev_1.3.1-1_amd64.deb ...
Unpacking libgles-dev:amd64 (1.3.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libgles-dev_1.3.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/GLES2/gl2.h', which is also in package libgles2-mesa-dev:amd64 20.0.8-0ubuntu1~18.04.1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libglx-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libgl-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libegl-dev_1.3.1-1_amd64.deb
 /var/cache/apt/archives/libgles-dev_1.3.1-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of libglvnd-dev:amd64:
 libglvnd-dev:amd64 depends on libegl-dev (>= 1.3.0-1); however:
  Package libegl-dev:amd64 is not installed.
 libglvnd-dev:amd64 depends on libgl-dev (>= 1.3.0-1); however:
  Package libgl-dev:amd64 is not installed.
 libglvnd-dev:amd64 depends on libgles-dev (>= 1.3.0-1); however:
  Package libgles-dev:amd64 is not installed.
 libglvnd-dev:amd64 depends on libglx-dev (>= 1.3.0-1); however:
  Package libglx-dev:amd64 is not installed.


dpkg: error processing package libglvnd-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libglvnd-dev:amd64
Press Return to continue, 'q' followed by Return to quit.



```=======================


```
**sudo apt-get autoremove**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 appmenu-qt : Depends: libqtcore4 (>= 4:4.8) but it is not installed
 carla-git : Depends: libqtcore4 (>= 4:4.5.3) but it is not installed
 grass-core : Depends: libgdal20 (>= 2.2.0) but it is not installed
 jackd : Depends: jackd2 but it is not installed or
                  jackd1 but it is not installed
 libalgorithms1 : Depends: gdal-abi-2-4-0
                  Depends: libgdal20 (>= 2.0.1) but it is not installed
 libdbusmenu-qt2 : Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installed
 libgdal-grass : Depends: gdal-abi-2-4-0
                 Depends: libgdal20 (>= 2.4.2) but it is not installed
 libglvnd-dev : Depends: libegl-dev (>= 1.3.0-1) but it is not installed
                Depends: libgl-dev (>= 1.3.0-1)
                Depends: libgles-dev (>= 1.3.0-1) but it is not installed
                Depends: libglx-dev (>= 1.3.0-1) but it is not installed
 libgmt5 : Depends: libgdal20 (>= 2.1.0) but it is not installed
 libimageclasses1 : Depends: gdal-abi-2-4-0
                    Depends: libgdal20 (>= 2.3.0) but it is not installed
 libmapcache1 : Depends: libgdal20 (>= 2.0.1) but it is not installed
 libopencv-imgcodecs3.2 : Depends: gdal-abi-2-4-0
                          Depends: libgdal20 (>= 2.0.1) but it is not installed
 libopenscenegraph-3.4-131 : Depends: gdal-abi-2-4-0
                             Depends: libgdal20 (>= 2.3.0) but it is not installed
 libopenscenegraph100v5 : Depends: gdal-abi-2-4-0
                          Depends: libgdal20 (>= 2.3.0) but it is not installed
                          Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installed
 libosgearth5 : Depends: gdal-abi-2-4-0
                Depends: libgdal20 (>= 2.0.1) but it is not installed
 libosgearthfeatures5 : Depends: libgdal20 (>= 2.2.0) but it is not installed
 libosgearthutil5 : Depends: libgdal20 (>= 1.10.1~) but it is not installed
 libpdal-base8 : Depends: gdal-abi-2-4-0
                 Depends: libgdal20 (>= 2.3.0) but it is not installed
 libpdal-plugin-sqlite : Depends: libgdal20 (>= 2.2) but it is not installed
 libqgis-analysis3.4.10 : Depends: gdal-abi-2-4-0
                          Depends: libgdal20 (>= 1.11) but it is not installed
 libqgis-app3.4.10 : Depends: libgdal20 (>= 2.0.1) but it is not installed
 libqgis-core3.4.10 : Depends: libgdal20 (>= 2.2.0) but it is not installed
 libqgis-gui3.4.10 : Depends: libgdal20 (>= 2.1.0) but it is not installed
 libqt4-declarative : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-designer : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-dev : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
              Recommends: libqt4-opengl-dev (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-dev-bin : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-help : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-network : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-opengl : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-qt3support : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-script : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-scripttools : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-sql : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-sql-sqlite : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-svg : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-test : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-xml : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqt4-xmlpatterns : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqtassistantclient4 : Depends: libqtcore4 (>= 4:4.8.1) but it is not installed
 libqtdbus4 : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 libqtgui4 : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 mapcache-tools : Depends: libgdal20 (>= 1.10.0-0~) but it is not installed
 openscenegraph : Depends: libqtcore4 (>= 4:4.5.3) but it is not installed
 pktools : Depends: gdal-abi-2-4-0
           Depends: libgdal20 (>= 2.3.0) but it is not installed
 postgis : Depends: libgdal20 (>= 2.0.1) but it is not installed
 postgresql-11-postgis-2.5 : Depends: libgdal20 (>= 2.0.1) but it is not installed
 pprepair : Depends: gdal-abi-2-4-0
            Depends: libgdal20 (>= 2.3.0) but it is not installed
            Recommends: prepair but it is not installed
 python-qt4 : Depends: libqtcore4 (>= 4:4.8.0-1~) but it is not installed
 qdbus : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 qt-at-spi : Depends: libqtcore4 (>= 4:4.8~) but it is not installed
 qt4-linguist-tools : Depends: libqtcore4 (= 4:4.8.7+dfsg-7ubuntu3) but it is not installed
 saga : Depends: libgdal20 (>= 2.0.1) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).





```

---

### Post by shantiq on 2020-07-17
solved and marked as such


ok so Aptitude or Synaptic or ```
sudo apt-get install -f
```   were going nowhere; then i decided to go to Synaptic again and enter "Fossa" ; it showed 2 wallpapers packages I put those through and THAT UNLOCKED some of the processes; then it was a case of running
sudo aptitude   went some of the way then moaned then ran ```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove
``` twice it did not finish in one go then ran ```
sudo apt-get install -f
``` and one more ```
sudo apt-get dist-upgrade && sudo apt-get autoremove
```  and all good it seems no broken anything anymore kinks ironed out

[ATTACH=CONFIG]286482[/ATTACH]




always a nerve-wracking experience are upgrades. Maybe just me ...

---

