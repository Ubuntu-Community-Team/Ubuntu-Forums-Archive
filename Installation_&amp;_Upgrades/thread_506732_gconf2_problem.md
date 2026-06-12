---
title: "gconf2 problem"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by bvidinli on 2007-07-22
i use gutsy alpha3,
when i try to update, i cannot complete update about gconf2.

i tried console, and i got:

root@bvidinli-laptop:/home/bvidinli# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libgpod1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gconf2
The following packages will be upgraded:
  gconf2
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
8 not fully installed or removed.
Need to get 0B/1262kB of archives.
After unpacking 4977kB of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  gconf2
Install these packages without verification [y/N]? y
(Reading database ... 183013 files and directories currently installed.)
Preparing to replace gconf2 2.19.1-1ubuntu1 (using .../gconf2_1%3a2.8.1-1warp_i386.deb) ...
Unpacking replacement gconf2 ...
dpkg: error processing /var/cache/apt/archives/gconf2_1%3a2.8.1-1warp_i386.deb (--unpack):
 trying to overwrite `/usr/share/sgml/gconf/gconf-1.0.dtd', which is also in package gconf2-common
Errors were encountered while processing:
 /var/cache/apt/archives/gconf2_1%3a2.8.1-1warp_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



i deleted /var/cache/apt/archives/gconf2_1%3a2.8.1-1warp_i386.deb 
and re-tried, but same error occured.

do you have any idea ?

---

### Post by bvidinli on 2007-07-22
now:


root@bvidinli-laptop:/home/bvidinli# dpkg -i --force-overwrite /var/cache/apt/archives/gconf2_1%3a2.8.1-1warp_i386.deb
(Reading database ... 183013 files and directories currently installed.)
Preparing to replace gconf2 2.19.1-1ubuntu1 (using .../gconf2_1%3a2.8.1-1warp_i386.deb) ...
Unpacking replacement gconf2 ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/sgml/gconf/gconf-1.0.dtd', which is also in package gconf2-common
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on libgconf2-4 (>= 2.8.1); however:
  Package libgconf2-4 is not configured yet.
dpkg: error processing gconf2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
root@bvidinli-laptop:/home/bvidinli# 



not solved yet.

---

### Post by bvidinli on 2007-07-22
root@bvidinli-laptop:/home/bvidinli# dpkg-reconfigure gnome-panel-data
/usr/sbin/dpkg-reconfigure: gnome-panel-data is broken or not fully installed
root@bvidinli-laptop:/home/bvidinli# apt-get install gnome-panel-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-panel-data is already the newest version.
The following packages were automatically installed and are no longer required:
  libgpod1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (1:2.19.5-0ubuntu3) ...
/var/lib/dpkg/info/gnome-panel-data.postinst: 26: gconf-schemas: not found
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.19); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.20); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 ebox
 gnome-panel-data
 gnome-panel
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


not solved yet....

---

### Post by bvidinli on 2007-07-22
almost solved, but update-manager does not startup yet...

in summary, 
i removed gnome-panel-data and some useless programs... then, it seems to be resolved...

here is output:


root@bvidinli-laptop:/home/bvidinli# aptitude remove gnome-panel-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  gnome-panel 
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
The following packages will be REMOVED:
  gnome-panel-data 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 12.0MB will be freed.
The following packages have unmet dependencies:
  gnome-panel: Depends: gnome-panel-data (>= 1:2.19) but it is not installable
               Depends: gnome-panel-data (< 1:2.20) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
alacarte
gnome-applets
gnome-panel
ubuntu-desktop

Leave the following dependencies unresolved:
gnome-session recommends gnome-panel
gdesklets-data recommends gnome-panel
Score is -1754

Accept this solution? [Y/n/q/?] 
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages will be automatically REMOVED:
  alacarte gnome-applets gnome-panel ubuntu-desktop 
The following packages have been kept back:
  monodevelop 
The following packages will be REMOVED:
  alacarte gnome-applets gnome-panel gnome-panel-data ubuntu-desktop 
0 packages upgraded, 0 newly installed, 5 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 15.3MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 182565 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gnome-applets ...
Removing alacarte ...
Removing gnome-panel ...
Removing gnome-panel-data ...
/var/lib/dpkg/info/gnome-panel-data.prerm: 6: gconf-schemas: not found
dpkg: error processing gnome-panel-data (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-panel-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 ebox
root@bvidinli-laptop:/home/bvidinli# aptitude remove gnome-panel-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
The following packages will be REMOVED:
  gnome-panel-data 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 12.0MB will be freed.
Writing extended state information... Done
(Reading database ... 182476 files and directories currently installed.)
Removing gnome-panel-data ...
/var/lib/dpkg/info/gnome-panel-data.prerm: 6: gconf-schemas: not found
dpkg: error processing gnome-panel-data (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-panel-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 ebox
root@bvidinli-laptop:/home/bvidinli# aptitude remove gnome-panel-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
The following packages will be REMOVED:
  gnome-panel-data 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 12.0MB will be freed.
Writing extended state information... Done
(Reading database ... 182476 files and directories currently installed.)
Removing gnome-panel-data ...
/var/lib/dpkg/info/gnome-panel-data.prerm: 6: gconf-schemas: not found
dpkg: error processing gnome-panel-data (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-panel-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 ebox
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# ai alacarte gnome-applets gnome-panel gnome-panel-data ubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following NEW packages will be automatically installed:
  gnome-applets gnome-panel imagemagick menu menu-xdg 
The following packages have been kept back:
  monodevelop 
The following NEW packages will be installed:
  alacarte gnome-applets gnome-panel imagemagick menu menu-xdg 
0 packages upgraded, 6 newly installed, 0 to remove and 2 not upgraded.
Need to get 1548kB/2011kB of archives. After unpacking 8294kB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/main gnome-applets 2.18.0-3ubuntu7 [324kB]
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/main alacarte 0.11.3-1ubuntu1 [71.9kB]
Get:3 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/main imagemagick 7:6.2.4.5.dfsg1-1 [739kB]
Get:4 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe menu 2.1.34 [409kB]                                                         
Get:5 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) gutsy/universe menu-xdg 0.2.3 [4584B]                                                      
Fetched 1548kB in 8s (175kB/s)                                                                                                
Preconfiguring packages ...
Selecting previously deselected package gnome-panel.
(Reading database ... 182477 files and directories currently installed.)
Unpacking gnome-panel (from .../gnome-panel_1%3a2.19.5-0ubuntu3_i386.deb) ...
Selecting previously deselected package gnome-applets.
Unpacking gnome-applets (from .../gnome-applets_2.18.0-3ubuntu7_i386.deb) ...
Selecting previously deselected package alacarte.
Unpacking alacarte (from .../alacarte_0.11.3-1ubuntu1_all.deb) ...
Selecting previously deselected package imagemagick.
Unpacking imagemagick (from .../imagemagick_7%3a6.2.4.5.dfsg1-1_i386.deb) ...
Selecting previously deselected package menu.
Unpacking menu (from .../archives/menu_2.1.34_i386.deb) ...
Selecting previously deselected package menu-xdg.
Unpacking menu-xdg (from .../menu-xdg_0.2.3_all.deb) ...
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel (1:2.19.5-0ubuntu3) ...

Setting up gnome-applets (2.18.0-3ubuntu7) ...

Setting up alacarte (0.11.3-1ubuntu1) ...

Setting up imagemagick (7:6.2.4.5.dfsg1-1) ...

Setting up menu (2.1.34) ...

Setting up menu-xdg (0.2.3) ...

Errors were encountered while processing:
 runit
 ebox
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ebox:
 ebox depends on runit; however:
  Package runit is not configured yet.
dpkg: error processing ebox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 runit
 ebox
root@bvidinli-laptop:/home/bvidinli# aptitude remove ebox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  libapache-authcookie-perl libapache-request-perl libapache-singleton-perl libapache2-mod-perl2 libcache-cache-perl 
  libclass-container-perl libclass-data-inheritable-perl libclone-perl libdbd-pg-perl libdevel-stacktrace-perl libebox 
  liberror-perl libexception-class-perl libfile-slurp-perl libfile-tail-perl libgnome2-gconf-perl libhtml-mason-perl 
  libintl-perl libipc-shareable-perl libipc-sharelite-perl liblog-dispatch-perl liblog-log4perl-perl libnet-ip-perl 
  libparams-validate-perl libperl6-junction-perl libpq4 libproc-process-perl libproc-processtable-perl libreadonly-perl 
  libreadonly-xs-perl libsys-cpu-perl libsys-cpuload-perl postgresql postgresql-8.2 postgresql-client-8.2 
  postgresql-client-common postgresql-common 
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
The following packages will be REMOVED:
  ebox 
0 packages upgraded, 0 newly installed, 38 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 35.4MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 182900 files and directories currently installed.)
Removing ebox ...
grep: /etc/inittab: No such file or directory
Removing libapache-authcookie-perl ...
Removing libapache-request-perl ...
Removing libapache-singleton-perl ...
Removing libapache2-mod-perl2 ...
Module perl already disabled
Removing libebox ...
Removing libhtml-mason-perl ...
Removing libcache-cache-perl ...
Removing libclass-container-perl ...
Removing libexception-class-perl ...
Removing libclass-data-inheritable-perl ...
Removing libclone-perl ...
Removing libdbd-pg-perl ...
Removing libdevel-stacktrace-perl ...
Removing liberror-perl ...
Removing libfile-slurp-perl ...
Removing libfile-tail-perl ...
Removing libgnome2-gconf-perl ...
Removing libintl-perl ...
Removing libipc-shareable-perl ...
Removing libipc-sharelite-perl ...
Removing liblog-dispatch-perl ...
Removing liblog-log4perl-perl ...
Removing libnet-ip-perl ...
Removing libparams-validate-perl ...
Removing libperl6-junction-perl ...
Removing libpq4 ...
Removing libproc-process-perl ...
Removing libproc-processtable-perl ...
Removing libreadonly-xs-perl ...
Removing libreadonly-perl ...
Removing libsys-cpu-perl ...
Removing libsys-cpuload-perl ...
Removing postgresql ...
Removing postgresql-8.2 ...
 * Stopping PostgreSQL 8.2 database server                                                                             [ OK ] 
Removing postgresql-client-8.2 ...
Removing postgresql-common ...
Removing postgresql-client-common ...
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up runit (1.6.0-1) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing runit (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 runit
root@bvidinli-laptop:/home/bvidinli# aptitude remove runit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
The following packages will be REMOVED:
  runit 
0 packages upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 487kB will be freed.
Writing extended state information... Done
(Reading database ... 180892 files and directories currently installed.)
Removing runit ...
grep: /etc/inittab: No such file or directory
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# aptitude remove runit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# ai alacarte gnome-applets gnome-panel gnome-panel-data ubuntu-desktop 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  vmware-player-kernel-modules 
The following packages have been kept back:
  monodevelop 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgpod1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@bvidinli-laptop:/home/bvidinli# 



root@bvidinli-laptop:/home/bvidinli# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgpod1
The following packages will be REMOVED:
  libgpod1
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 369kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 180836 files and directories currently installed.)
Removing libgpod1 ...
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# 
root@bvidinli-laptop:/home/bvidinli# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@bvidinli-laptop:/home/bvidinli#

---

