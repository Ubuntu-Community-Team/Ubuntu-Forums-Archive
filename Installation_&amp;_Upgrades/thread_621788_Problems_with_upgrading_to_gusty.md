---
title: "Problems with upgrading to gusty"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by almackska on 2007-11-24
I am not the kind of guy who posts a question as soon as i have a problem, I google the heck out of it and usualy i find an answer. But for weeks i have been trying to upgrade to gusty, I have removed envy, compiz and programs like that and i have redone my source.list like 20 times. And i get this problem. 


Getting upgrade prerequisites failed

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

here is the output of those files

APT,LOG
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing apache2.2-common as dep of apache2-mpm-prefork
Installing openoffice.org-common as dep of openoffice.org-style-human
Installing libpng12-0 as dep of libpng12-dev
Installing amarok as dep of amarok-xine
Installing libmagic1 as dep of file
Installing libfreetype6 as dep of libfreetype6-dev
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing php5-common as dep of php5-mysql
Installing hal as dep of gnome-mount
Starting
Starting 2
Investigating openoffice.org-base
Package openoffice.org-base has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-base 2
  Removing openoffice.org-base rather than change openoffice.org-core
Investigating libvorbis-dev
Package libvorbis-dev has broken dep on libvorbis0a
  Considering libvorbis0a 119 as a solution to libvorbis-dev 2
  Removing libvorbis-dev rather than change libvorbis0a
Investigating openoffice.org-filter-mobiledev
Package openoffice.org-filter-mobiledev has broken dep on openoffice.org-java-common
  Considering openoffice.org-java-common 6 as a solution to openoffice.org-filter-mobiledev 1
  Removing openoffice.org-filter-mobiledev rather than change openoffice.org-java-common
Investigating openoffice.org-gtk
Package openoffice.org-gtk has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-gtk 1
  Removing openoffice.org-gtk rather than change openoffice.org-core
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 7 as a solution to libpoppler1-glib 1
  Removing libpoppler1-glib rather than change libpoppler1
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-gnome 0
  Removing openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-evolution 0
  Removing openoffice.org-evolution rather than change openoffice.org-core
Investigating boson
Package boson has broken dep on libvorbis-dev
  Considering libvorbis-dev 2 as a solution to boson 0
  Removing boson rather than change libvorbis-dev
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org 0
  Removing openoffice.org rather than change openoffice.org-core
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 13 as a solution to firefox-gnome-support 0
  Removing firefox-gnome-support rather than change firefox
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 0
  Removing evince rather than change libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 1 as a solution to gnome-app-install 0
  Removing gnome-app-install rather than change app-install-data
Investigating libsdl-mixer1.2-dev
Package libsdl-mixer1.2-dev has broken dep on libvorbis-dev
  Considering libvorbis-dev 2 as a solution to libsdl-mixer1.2-dev 0
  Removing libsdl-mixer1.2-dev rather than change libvorbis-dev
Investigating hal-info
Package hal-info has broken dep on hal
  Considering hal 11 as a solution to hal-info -1
  Removing hal-info rather than change hal
Done
Installing vim-tiny as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing desktop-effects as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing evince as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-app-install as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing brltty as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing brltty-x11 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing firefox-gnome-support as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing network-manager-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing network-manager as dep of network-manager-gnome
Installing openoffice.org as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-evolution as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing totem-mozilla as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 2
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 2 as a solution to gnome-app-install 2
  Removing gnome-app-install rather than change app-install-data
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 1
  Removing libpoppler1-glib rather than change libpoppler1
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 28 as a solution to openoffice.org-gnome 0
  Removing openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 28 as a solution to openoffice.org-evolution 0
  Removing openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 28 as a solution to openoffice.org 0
  Removing openoffice.org rather than change openoffice.org-core
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 14 as a solution to firefox-gnome-support 0
  Removing firefox-gnome-support rather than change firefox
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on gnome-app-install
  Considering gnome-app-install 2 as a solution to ubuntu-desktop 9999
  Added gnome-app-install to the remove list
  Fixing ubuntu-desktop via keep of gnome-app-install
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 2
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 2 as a solution to gnome-app-install 2
  Removing gnome-app-install rather than change app-install-data
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 1
  Removing libpoppler1-glib rather than change libpoppler1
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on gnome-app-install
  Considering gnome-app-install 2 as a solution to ubuntu-desktop 9999
  Added gnome-app-install to the remove list
  Fixing ubuntu-desktop via keep of gnome-app-install
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 2
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 2 as a solution to gnome-app-install 9999
  Added app-install-data to the remove list
  Fixing gnome-app-install via keep of app-install-data
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 2
  Removing libpoppler1-glib rather than change libpoppler1
 Try to Re-Instate app-install-data
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 4 as a solution to evince 2
  Removing evince rather than change libpoppler1-glib
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on evince
  Considering evince 4 as a solution to ubuntu-desktop 9999
  Added evince to the remove list
  Fixing ubuntu-desktop via keep of evince
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 4 as a solution to evince 9999
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 9999
  Added libpoppler1 to the remove list
  Fixing libpoppler1-glib via keep of libpoppler1
 Try to Re-Instate libpoppler1
Done
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 81, in <module>
    if controler.askDistUpgrade():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeControler.py", line 595, in askDistUpgrade
    if not self.cache.distUpgrade(self._view, self.serverMode, self.logfd):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 330, in distUpgrade
    if not origin.trusted:

UnboundLocalError: local variable 'origin' referenced before assignment

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2007-08-23 18:59:41.557 Using runtime prefix = /usr
2007-08-23 18:59:41.563 DPMS is active.
2007-08-23 18:59:41.575 New DB connection, total: 1
2007-08-23 18:59:41.580 Connected to database 'mythconverg' at host: localhost
2007-08-23 18:59:41.582 Total desktop dim: 1024x768, with 2 screen[s].
2007-08-23 18:59:41.606 Using screen 0, 1024x768 at 0,0
2007-08-23 18:59:41.625 Current Schema Version: 1160
2007-08-23 18:59:41.636 mythfrontend version: 0.20.20060828-4 [www.mythtv.org](www.mythtv.org)
2007-08-23 18:59:41.637 Enabled verbose msgs:  important general
2007-08-23 18:59:42.165 Total desktop dim: 1024x768, with 2 screen[s].
2007-08-23 18:59:42.185 Using screen 0, 1024x768 at 0,0
2007-08-23 18:59:42.186 Switching to square mode (blue)
2007-08-23 18:59:42.200 Using the OpenGL painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv2007-08-23 18:59:42.574 Joystick disabled.
, see preceding messages
2007-08-23 18:59:59.779 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-08-23 19:00:01.291 Registering Internal as a media playback plugin.
2007-08-23 19:00:01.318 Mediamonitor: Adding /dev/hdc
2007-08-23 19:00:01.330 Mediamonitor: AddDevice() -- Not adding '/dev/hdc', it appears to be a duplicate.
2007-08-23 19:00:01.334 Starting media monitor.
2007-08-23 19:00:01.625 Using NV NPOT texture extension
2007-08-23 19:00:04.515 New DB connection, total: 2
2007-08-23 19:00:04.521 Connected to database 'mythconverg' at host: localhost
2007-08-23 19:00:04.561 Connecting to backend server: 192.168.2.2:6543 (try 1 of 5)
2007-08-23 19:00:05.880 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
2007-08-23 19:00:06.020 TV: Attempting to change from None to None
2007-08-23 19:00:08.195 Connecting to backend server: 192.168.2.2:6543 (try 1 of 5)
2007-08-23 19:00:09.005 Connection timed out.          
			You probably should modify the Master Server 
			settings in the setup program and set the    
			proper IP address.
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing apache2.2-common as dep of apache2-mpm-prefork
Installing openoffice.org-common as dep of openoffice.org-style-human
Installing libpng12-0 as dep of libpng12-dev
Installing amarok as dep of amarok-xine
Installing libmagic1 as dep of file
Installing libfreetype6 as dep of libfreetype6-dev
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing php5-common as dep of php5-mysql
Installing hal as dep of gnome-mount
Starting
Starting 2
Investigating openoffice.org-base
Package openoffice.org-base has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-base 2
  Removing openoffice.org-base rather than change openoffice.org-core
Investigating libvorbis-dev
Package libvorbis-dev has broken dep on libvorbis0a
  Considering libvorbis0a 119 as a solution to libvorbis-dev 2
  Removing libvorbis-dev rather than change libvorbis0a
Investigating openoffice.org-filter-mobiledev
Package openoffice.org-filter-mobiledev has broken dep on openoffice.org-java-common
  Considering openoffice.org-java-common 6 as a solution to openoffice.org-filter-mobiledev 1
  Removing openoffice.org-filter-mobiledev rather than change openoffice.org-java-common
Investigating openoffice.org-gtk
Package openoffice.org-gtk has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-gtk 1
  Removing openoffice.org-gtk rather than change openoffice.org-core
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 7 as a solution to libpoppler1-glib 1
  Removing libpoppler1-glib rather than change libpoppler1
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-gnome 0
  Removing openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org-evolution 0
  Removing openoffice.org-evolution rather than change openoffice.org-core
Investigating boson
Package boson has broken dep on libvorbis-dev
  Considering libvorbis-dev 2 as a solution to boson 0
  Removing boson rather than change libvorbis-dev
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 33 as a solution to openoffice.org 0
  Removing openoffice.org rather than change openoffice.org-core
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 13 as a solution to firefox-gnome-support 0
  Removing firefox-gnome-support rather than change firefox
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 0
  Removing evince rather than change libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 1 as a solution to gnome-app-install 0
  Removing gnome-app-install rather than change app-install-data
Investigating libsdl-mixer1.2-dev
Package libsdl-mixer1.2-dev has broken dep on libvorbis-dev
  Considering libvorbis-dev 2 as a solution to libsdl-mixer1.2-dev 0
  Removing libsdl-mixer1.2-dev rather than change libvorbis-dev
Investigating hal-info
Package hal-info has broken dep on hal
  Considering hal 11 as a solution to hal-info -1
  Removing hal-info rather than change hal
Done
Installing vim-tiny as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing desktop-effects as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing evince as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gnome-app-install as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing brltty as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing brltty-x11 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing firefox-gnome-support as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing network-manager-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing network-manager as dep of network-manager-gnome
Installing openoffice.org as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-evolution as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing totem-mozilla as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 2
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 2 as a solution to gnome-app-install 2
  Removing gnome-app-install rather than change app-install-data
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 1
  Removing libpoppler1-glib rather than change libpoppler1
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 28 as a solution to openoffice.org-gnome 0
  Removing openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-core
  Considering openoffice.org-core 28 as a solution to openoffice.org-evolution 0
  Removing openoffice.org-evolution rather than change openoffice.org-core
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-core
  Considering openoffice.org-core 28 as a solution to openoffice.org 0
  Removing openoffice.org rather than change openoffice.org-core
Investigating firefox-gnome-support
Package firefox-gnome-support has broken dep on firefox
  Considering firefox 14 as a solution to firefox-gnome-support 0
  Removing firefox-gnome-support rather than change firefox
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on gnome-app-install
  Considering gnome-app-install 2 as a solution to ubuntu-desktop 9999
  Added gnome-app-install to the remove list
  Fixing ubuntu-desktop via keep of gnome-app-install
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 2
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 2 as a solution to gnome-app-install 2
  Removing gnome-app-install rather than change app-install-data
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 1
  Removing libpoppler1-glib rather than change libpoppler1
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on gnome-app-install
  Considering gnome-app-install 2 as a solution to ubuntu-desktop 9999
  Added gnome-app-install to the remove list
  Fixing ubuntu-desktop via keep of gnome-app-install
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 1 as a solution to evince 2
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating gnome-app-install
Package gnome-app-install has broken dep on app-install-data
  Considering app-install-data 2 as a solution to gnome-app-install 9999
  Added app-install-data to the remove list
  Fixing gnome-app-install via keep of app-install-data
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 2
  Removing libpoppler1-glib rather than change libpoppler1
 Try to Re-Instate app-install-data
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 4 as a solution to evince 2
  Removing evince rather than change libpoppler1-glib
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on evince
  Considering evince 4 as a solution to ubuntu-desktop 9999
  Added evince to the remove list
  Fixing ubuntu-desktop via keep of evince
Investigating evince
Package evince has broken dep on libpoppler1-glib
  Considering libpoppler1-glib 4 as a solution to evince 9999
  Added libpoppler1-glib to the remove list
  Fixing evince via keep of libpoppler1-glib
Investigating libpoppler1-glib
Package libpoppler1-glib has broken dep on libpoppler1
  Considering libpoppler1 4 as a solution to libpoppler1-glib 9999
  Added libpoppler1 to the remove list
  Fixing libpoppler1-glib via keep of libpoppler1
 Try to Re-Instate libpoppler1
Done
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 81, in <module>
    if controler.askDistUpgrade():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeControler.py", line 595, in askDistUpgrade
    if not self.cache.distUpgrade(self._view, self.serverMode, self.logfd):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 330, in distUpgrade
    if not origin.trusted:

UnboundLocalError: local variable 'origin' referenced before assignment

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
Installing compiz-core as dep of compiz-plugins
Installing compiz-gnome as dep of compiz
Starting
Starting 2
Investigating compiz-gtk
Package compiz-gtk has broken dep on compiz-core
  Considering compiz-core 7 as a solution to compiz-gtk 0
  Removing compiz-gtk rather than change compiz-core
Done
Installing vim-tiny as dep of ubuntu-minimal
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing desktop-effects as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing evince as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpoppler1-glib as dep of evince
Installing gnome-app-install as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing brltty as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing brltty-x11 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing firefox-gnome-support as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing network-manager-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing network-manager as dep of network-manager-gnome
Installing openoffice.org as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-base as dep of openoffice.org
Installing openoffice.org-filter-mobiledev as dep of openoffice.org
Installing openoffice.org-evolution as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing openoffice.org-gtk as dep of openoffice.org-gnome
Installing totem-mozilla as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
ERROR:root:IOError in cache.commit(): 'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-tiny_7.0-164+1ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-tiny_7.0-164+1ubuntu7.2_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_1.43_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_1.43_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/desktop-effects/desktop-effects_0.7.1-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/desktop-effects/desktop-effects_0.7.1-0ubuntu4_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.8.1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_0.8.1-0ubuntu1_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4). - connect (101 Network is unreachable) [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.6+1-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.6+1-0ubuntu1_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.3.31_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.3.31_all.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.4-6ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.4-6ubuntu7_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.4-6ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager-gnome_0.6.4-6ubuntu7_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.2.0-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.2.0-1ubuntu4_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-filter-mobiledev_2.2.0-1ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-filter-mobiledev_2.2.0-1ubuntu4_all.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4). - connect (101 Network is unreachable) [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.2.0-1ubuntu4_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.2.0-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.2.0-1ubuntu4_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4). - connect (101 Network is unreachable) [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.2.0-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.2.0-1ubuntu4_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.2.0-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.2.0-1ubuntu4_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4). - connect (101 Network is unreachable) [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.18.1-0ubuntu3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.18.1-0ubuntu3_all.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.43_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-desktop_1.43_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty_3.7.2-7ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty_3.7.2-7ubuntu3_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty-x11_3.7.2-7ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/brltty/brltty-x11_3.7.2-7ubuntu3_i386.deb) Could not connect to us.archive.ubuntu.com:80 (91.36.0.4), connection timed out [IP: 91.36.0.4 80]
'. Retrying (currentTry: 0)
The application 'update-manager' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
Installing libopal-2.2 as dep of ekiga
Installing hal-info as dep of hal
Installing libntfs-3g9 as dep of ntfs-3g
Starting
Starting 2
Investigating libfaad2-0
Package libfaad2-0 has broken dep on libfaad0
Investigating libopal-2.2
Package libopal-2.2 has broken dep on libopal-2.2.0
  Considering libopal-2.2.0 -1 as a solution to libopal-2.2 0
  Added libopal-2.2.0 to the remove list
  Fixing libopal-2.2 via remove of libopal-2.2.0
 Try to Re-Instate libfaad2-0
Done
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 81, in <module>
    if controler.askDistUpgrade():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeControler.py", line 595, in askDistUpgrade
    if not self.cache.distUpgrade(self._view, self.serverMode, self.logfd):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 300, in distUpgrade
    if not self._installMetaPkgs(view):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 424, in _installMetaPkgs
    self[pkg].markInstall()

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 81, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-minimal'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook
totem-video-thumbnailer couln't open file 'file:///home/mack/The%20Shins/Chutes%20too%20Narrow/04%20-%20Young%20Pilgrams.ogg'
Reason: This is an audio-only file, and there is no audio output available..
Installing libopal-2.2 as dep of ekiga
Installing hal-info as dep of hal
Installing libntfs-3g9 as dep of ntfs-3g
Starting
Starting 2
Investigating libfaad2-0
Package libfaad2-0 has broken dep on libfaad0
Investigating libopal-2.2
Package libopal-2.2 has broken dep on libopal-2.2.0
  Considering libopal-2.2.0 -1 as a solution to libopal-2.2 0
  Added libopal-2.2.0 to the remove list
  Fixing libopal-2.2 via remove of libopal-2.2.0
 Try to Re-Instate libfaad2-0
Done
ERROR:root:not handled expection:
Traceback (most recent call last):

  File "/usr/bin/update-manager", line 81, in <module>
    if controler.askDistUpgrade():

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeControler.py", line 595, in askDistUpgrade
    if not self.cache.distUpgrade(self._view, self.serverMode, self.logfd):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 300, in distUpgrade
    if not self._installMetaPkgs(view):

  File "/usr/lib/python2.5/site-packages/DistUpgrade/DistUpgradeCache.py", line 424, in _installMetaPkgs
    self[pkg].markInstall()

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 81, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-minimal'

ERROR:root:failed to import apport python module, can't report bug: No module named python_hook

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format



---------------------------------------------------------------------------------------------


MAIN.LOG


2007-11-24 00:13:39,141 INFO release-upgrader version '0.81' started
2007-11-24 00:13:40,228 DEBUG lsb-release: 'feisty'
2007-11-24 00:13:40,228 DEBUG _pythonSymlinkCheck run
2007-11-24 00:13:41,068 DEBUG checkViewDepends()
2007-11-24 00:13:41,069 DEBUG getRequiredBackports()
2007-11-24 00:13:45,627 DEBUG marking 'release-upgrader-apt' for install
2007-11-24 00:13:45,721 DEBUG marking 'release-upgrader-dpkg' for install
2007-11-24 00:14:45,877 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 3 Complete: 0 Local: 0 IsTrusted: 0 FileSize: 1924684 DestFile:'/tmp/tmpZMuODK/backports/partial/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ub' 
2007-11-24 00:14:45,878 ERROR pre-requists item 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted


_____________________________________________________________________________________




I am stumped, i suppose the last line might explane it but how do i fix that?

---

### Post by zvacet on 2007-11-24
If you have any unofficial repository(like medibuntu or something else) in your source list put # in front of that line.Let your source look like this one

> ## See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse


```
sudo aptitude update
```

You can add your unofficial repos after upgrade.

---

### Post by almackska on 2007-11-24
I changed my source list to the one posted and i tried updating and i still get hung up at where i was before.

Im not sure this means anything, but when i update with update manager and i see the progress of downloading, I see allot of "failed". What do i do to determine the problem here? Any takers?

---

### Post by almackska on 2007-11-24
sorry, also, when i try to upgrade it hangs at fetching file 1 of 2 when its preparing to upgrade.

---

### Post by Pumalite on 2007-11-24
Try changing your server. If not, check your connection.

---

### Post by almackska on 2007-11-24
thnx, I have tried every server from, main to the local server here in portland. None work. In software sources i see that backports has a little " - ' on it and i cant deselect it. There a way to deselect the backports tab?

---

### Post by bapoumba on 2007-11-24
Could you please post your sources.list:
```
cat /etc/apt/sources.list
```
Can we assume your internet connection is working fine (browser etc..) ?

---

### Post by almackska on 2007-11-24
yes, my internet is pristene. :) 


mack@mack-desktop:~$ cat /etc/apt/sources.list
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty main restricted universe multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
mack@mack-desktop:~$

---

### Post by bapoumba on 2007-11-24
> **almackska said:**
> yes, my internet is pristene. :) 


mack@mack-desktop:~$ cat /etc/apt/sources.list
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty main restricted universe multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) feisty-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
mack@mack-desktop:~$
These are feisty repos. Your title states you are upgrading to gusty, is that what you wish to do?
If so, please try my source.list for gutsy:

```
# Base.
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

# Security.
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```
With the main repositories. You can switch back to a local one once you are all set up.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by almackska on 2007-11-24
capital idea...

Im trying it now. Looks promising.

---

### Post by almackska on 2007-11-24
I did what ya said doc, and im all better. Now i just need to find a good nvidia driver and repos to use.


Thank you very much for the help, i like the ubuntu support. Very quick. Next time i wont be as stubborn.

---

### Post by bapoumba on 2007-11-25
You're welcome, and I'm glad to see you got it to work :)

Would you have a "Restricted Driver Manager" menu somewhere ?

---

