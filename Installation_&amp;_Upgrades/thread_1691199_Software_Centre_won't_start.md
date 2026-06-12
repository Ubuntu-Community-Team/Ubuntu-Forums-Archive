---
title: "Software Centre won't start"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by dtaylorjones on 2011-02-19
Tried to start Software Centre today in Ubuntu 10.04 Netbook Edition.

It never started, showed the "starting software centre" message then stalled for a few moments and then nothing. 

"gksu software-center" in terminal returns this error;

```
dan@Viktor:~$ gksu software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 299, in _get_channels
    for channel_iter in self.db.xapiandb.allterms("XOL"):
  File "/usr/lib/python2.6/dist-packages/xapian.py", line 4769, in next
    self._iter.next()
xapian.DatabaseError: Error reading block 77: Input/output error

```I tried un-installing and then installing software centre multiple times from the terminal only to get the same problem.

Synaptic and update manager run fine and don't list Software Centre as a broken package and my system is up to date.

Any suggestions folks?

---

### Post by sikander3786 on 2011-02-19
Please go to Applications > Accessories > Terminal and paste the output of these commands.

```
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by dtaylorjones on 2011-02-19
> **sikander3786 said:**
> Please go to Applications > Accessories > Terminal and paste the output of these commands.

```
sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f
```

**sudo apt-get update && sudo apt-get upgrade** returns;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-assistant libpackagekit-glib2-12 libboost-program-options1.40.0 libqt4-test phonon kdesudo libpackagekit-qt-12 libakonadiprivate1 install-package libqt4-help
  python-qt4 python-sip python-packagekit packagekit gdebi-kde kdepimlibs5 update-manager-kde packagekit-backend-apt libqt4-scripttools kdepimlibs-data python-kde4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  deluge-common deluge-gtk libblas3gf libboost-filesystem1.40.0 libboost-python1.40.0 libboost-system1.40.0 libboost-thread1.40.0 libgfortran3 liblapack3gf libmikmod2
  libportmidi0 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 libtorrent-rasterbar5 python-chardet python-libtorrent python-numpy python-pygame
Suggested packages:
  libtorrent-rasterbar-dbg python-numpy-doc python-numpy-dbg python-nose
The following NEW packages will be installed
  deluge deluge-common deluge-gtk libblas3gf libboost-filesystem1.40.0 libboost-python1.40.0 libboost-system1.40.0 libboost-thread1.40.0 libgfortran3 liblapack3gf libmikmod2
  libportmidi0 libsdl-image1.2 libsdl-mixer1.2 libsdl-ttf2.0-0 libsmpeg0 libtorrent-rasterbar5 python-chardet python-libtorrent python-numpy python-pygame
0 upgraded, 21 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.2MB of archives.
After this operation, 36.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libboost-system1.40.0 1.40.0-4ubuntu4 [31.1kB]
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libboost-filesystem1.40.0 1.40.0-4ubuntu4 [51.9kB]
Get: 3 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libboost-python1.40.0 1.40.0-4ubuntu4 [139kB]
Get: 4 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libboost-thread1.40.0 1.40.0-4ubuntu4 [53.7kB]
Get: 5 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libtorrent-rasterbar5 0.14.10-1 [1,191kB]
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe python-libtorrent 0.14.10-1 [460kB]
Get: 7 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe python-chardet 2.0.1-1 [175kB]                                                                                       
Get: 8 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe deluge-common 1.2.2-2 [1,107kB]                                                                                      
Get: 9 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe deluge-gtk 1.2.2-2 [259kB]                                                                                           
Get: 10 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe deluge 1.2.2-2 [33.4kB]                                                                                             
Get: 11 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libgfortran3 4.4.3-4ubuntu5 [240kB]                                                                                     
Get: 12 http://gb.archive.ubuntu.com/ubuntu/ lucid/main libblas3gf 1.2-2build1 [211kB]                                                                                          
Get: 13 http://gb.archive.ubuntu.com/ubuntu/ lucid/main liblapack3gf 3.2.1-2 [3,089kB]                                                                                          
Get: 14 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe libmikmod2 3.1.11-a-6.1ubuntu0.1 [148kB]
Get: 15 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libportmidi0 1:200-0ubuntu1 [22.9kB]
Get: 16 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libsdl-image1.2 1.2.10-1 [32.6kB]
Get: 17 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libsmpeg0 0.4.5+cvs20030824-2.2 [102kB]
Get: 18 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libsdl-mixer1.2 1.2.8-6build1 [99.1kB]
Get: 19 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libsdl-ttf2.0-0 2.0.9-1build1 [16.4kB]
Get: 20 http://gb.archive.ubuntu.com/ubuntu/ lucid/main python-numpy 1:1.3.0-3build1 [1,244kB]
Get: 21 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe python-pygame 1.9.1release-0ubuntu1 [2,458kB]
Fetched 11.2MB in 23s (482kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package libboost-system1.40.0.
(Reading database ... 153253 files and directories currently installed.)
Unpacking libboost-system1.40.0 (from .../libboost-system1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libboost-filesystem1.40.0.
Unpacking libboost-filesystem1.40.0 (from .../libboost-filesystem1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libboost-python1.40.0.
Unpacking libboost-python1.40.0 (from .../libboost-python1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libboost-thread1.40.0.
Unpacking libboost-thread1.40.0 (from .../libboost-thread1.40.0_1.40.0-4ubuntu4_i386.deb) ...
Selecting previously deselected package libtorrent-rasterbar5.
Unpacking libtorrent-rasterbar5 (from .../libtorrent-rasterbar5_0.14.10-1_i386.deb) ...
Selecting previously deselected package python-libtorrent.
Unpacking python-libtorrent (from .../python-libtorrent_0.14.10-1_i386.deb) ...
Selecting previously deselected package python-chardet.
Unpacking python-chardet (from .../python-chardet_2.0.1-1_all.deb) ...
Selecting previously deselected package deluge-common.
Unpacking deluge-common (from .../deluge-common_1.2.2-2_all.deb) ...
Selecting previously deselected package deluge-gtk.
Unpacking deluge-gtk (from .../deluge-gtk_1.2.2-2_all.deb) ...
Selecting previously deselected package deluge.
Unpacking deluge (from .../deluge_1.2.2-2_all.deb) ...
Selecting previously deselected package libgfortran3.
Unpacking libgfortran3 (from .../libgfortran3_4.4.3-4ubuntu5_i386.deb) ...
Selecting previously deselected package libblas3gf.
Unpacking libblas3gf (from .../libblas3gf_1.2-2build1_i386.deb) ...
Selecting previously deselected package liblapack3gf.
Unpacking liblapack3gf (from .../liblapack3gf_3.2.1-2_i386.deb) ...
Selecting previously deselected package libmikmod2.
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6.1ubuntu0.1_i386.deb) ...
Selecting previously deselected package libportmidi0.
Unpacking libportmidi0 (from .../libportmidi0_1%3a200-0ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-1_i386.deb) ...
Selecting previously deselected package libsmpeg0.
Unpacking libsmpeg0 (from .../libsmpeg0_0.4.5+cvs20030824-2.2_i386.deb) ...
Selecting previously deselected package libsdl-mixer1.2.
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.8-6build1_i386.deb) ...
Selecting previously deselected package libsdl-ttf2.0-0.
Unpacking libsdl-ttf2.0-0 (from .../libsdl-ttf2.0-0_2.0.9-1build1_i386.deb) ...
Selecting previously deselected package python-numpy.
Unpacking python-numpy (from .../python-numpy_1%3a1.3.0-3build1_i386.deb) ...
Selecting previously deselected package python-pygame.
Unpacking python-pygame (from .../python-pygame_1.9.1release-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up libboost-system1.40.0 (1.40.0-4ubuntu4) ...

Setting up libboost-filesystem1.40.0 (1.40.0-4ubuntu4) ...

Setting up libboost-python1.40.0 (1.40.0-4ubuntu4) ...

Setting up libboost-thread1.40.0 (1.40.0-4ubuntu4) ...

Setting up libtorrent-rasterbar5 (0.14.10-1) ...

Setting up python-libtorrent (0.14.10-1) ...

Setting up python-chardet (2.0.1-1) ...

Setting up deluge-common (1.2.2-2) ...

Setting up deluge-gtk (1.2.2-2) ...

Setting up deluge (1.2.2-2) ...

Setting up libgfortran3 (4.4.3-4ubuntu5) ...

Setting up libblas3gf (1.2-2build1) ...

Setting up liblapack3gf (3.2.1-2) ...

Setting up libmikmod2 (3.1.11-a-6.1ubuntu0.1) ...

Setting up libportmidi0 (1:200-0ubuntu1) ...

Setting up libsdl-image1.2 (1.2.10-1) ...

Setting up libsmpeg0 (0.4.5+cvs20030824-2.2) ...

Setting up libsdl-mixer1.2 (1.2.8-6build1) ...

Setting up libsdl-ttf2.0-0 (2.0.9-1build1) ...

Setting up python-numpy (1:1.3.0-3build1) ...

Processing triggers for python-central ...
Setting up python-pygame (1.9.1release-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for python-central ...
dan@Viktor:~$ gksu software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 299, in _get_channels
    for channel_iter in self.db.xapiandb.allterms("XOL"):
  File "/usr/lib/python2.6/dist-packages/xapian.py", line 4769, in next
    self._iter.next()
xapian.DatabaseError: Error reading block 77: Input/output error
dan@Viktor:~$ gksudo software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 299, in _get_channels
    for channel_iter in self.db.xapiandb.allterms("XOL"):
  File "/usr/lib/python2.6/dist-packages/xapian.py", line 4769, in next
    self._iter.next()
xapian.DatabaseError: Error reading block 77: Input/output error
dan@Viktor:~$ clear

dan@Viktor:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for dan: 
Hit http://gb.archive.ubuntu.com lucid Release.gpg
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB          
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB    
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB    
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB  
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ lucid/partner Translation-en_GB              
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release                                 
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid Release                                 
Hit http://gb.archive.ubuntu.com lucid-updates Release                       
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                     
Hit http://gb.archive.ubuntu.com lucid/main Sources                            
Hit http://gb.archive.ubuntu.com lucid/restricted Sources            
Hit http://gb.archive.ubuntu.com lucid/universe Packages             
Hit http://gb.archive.ubuntu.com lucid/universe Sources              
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages           
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources            
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages         
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages   
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources          
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources    
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Get: 1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get: 2 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB
Get: 3 http://dl.google.com stable Release [1,347B]
Get: 4 http://dl.google.com stable Release [1,347B]
Get: 5 http://dl.google.com stable/main Packages [1,093B]
Get: 6 http://dl.google.com stable/main Packages [737B]
Fetched 4,918B in 0s (7,530B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```**sudo dpkg --configure -a **
returns nothing, just goes onto another line.

**sudo apt-get install -f** returns;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-assistant libpackagekit-glib2-12 libboost-program-options1.40.0
  libqt4-test phonon kdesudo libpackagekit-qt-12 libakonadiprivate1
  install-package libqt4-help python-qt4 python-sip python-packagekit
  packagekit gdebi-kde kdepimlibs5 update-manager-kde packagekit-backend-apt
  libqt4-scripttools kdepimlibs-data python-kde4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```Tried running **sudo apt-get update** as it suggests and got;

```
Hit http://security.ubuntu.com lucid-security Release.gpg
Hit http://archive.canonical.com lucid Release.gpg                                                
Ign http://archive.canonical.com/ lucid/partner Translation-en_GB                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release.gpg                           
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB        
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB                        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB                   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB                 
Hit http://archive.canonical.com lucid Release                                                     
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB                          
Hit http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg                   
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://security.ubuntu.com lucid-security Release                        
Hit http://gb.archive.ubuntu.com lucid Release                               
Hit http://gb.archive.ubuntu.com lucid-updates Release                                             
Hit http://archive.canonical.com lucid/partner Packages                                            
Hit http://security.ubuntu.com lucid-security/main Packages                                        
Hit http://gb.archive.ubuntu.com lucid/main Packages                                               
Hit http://security.ubuntu.com lucid-security/restricted Packages            
Hit http://security.ubuntu.com lucid-security/main Sources             
Hit http://security.ubuntu.com lucid-security/restricted Sources                             
Hit http://security.ubuntu.com lucid-security/universe Packages                              
Hit http://security.ubuntu.com lucid-security/universe Sources         
Hit http://security.ubuntu.com lucid-security/multiverse Packages                            
Hit http://gb.archive.ubuntu.com lucid/restricted Packages                                   
Hit http://gb.archive.ubuntu.com lucid/main Sources                                          
Hit http://gb.archive.ubuntu.com lucid/restricted Sources            
Hit http://gb.archive.ubuntu.com lucid/universe Packages             
Hit http://gb.archive.ubuntu.com lucid/universe Sources              
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages           
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources            
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages         
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources
Get: 1 http://dl.google.com stable Release.gpg [197B]
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get: 2 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_GB
Get: 3 http://dl.google.com stable Release [1,347B]                                                                                                                             
Get: 4 http://dl.google.com stable Release [1,347B]                                                                                                                             
Get: 5 http://dl.google.com stable/main Packages [1,093B]                                                                                                                       
Get: 6 http://dl.google.com stable/main Packages [737B]                                                                                                                         
Fetched 4,918B in 6s (732B/s)                                                                                                                                                   
Reading package lists... Done

```

---

### Post by sikander3786 on 2011-02-19
Thanks for the outputs.

Try removing and re-installing Software Center.

```
sudo apt-get remove --purge software-center
sudo apt-get install software-center
```

Please post the outputs as well and then try opening Software Center via GUI or Terminal.

---

### Post by dtaylorjones on 2011-02-19
Thanks. outputs shown below...
[B]
sudo apt-get remove --purge software-center[/B] returns;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  polkit-kde-1 libqt4-assistant libpackagekit-glib2-12
  libboost-program-options1.40.0 libqt4-test phonon kdesudo
  libpackagekit-qt-12 libakonadiprivate1 install-package libqt4-help
  python-qt4 python-sip python-packagekit packagekit gdebi-kde kdepimlibs5
  update-manager-kde packagekit-backend-apt libqt4-scripttools kdepimlibs-data
  python-kde4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  software-center*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,720kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154909 files and directories currently installed.)
Removing software-center ...
Purging configuration files for software-center ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for python-support ...
Processing triggers for python-central ...
```[B]
sudo apt-get install software-center[/B] returns;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-assistant libpackagekit-glib2-12 libboost-program-options1.40.0
  libqt4-test phonon kdesudo libpackagekit-qt-12 libakonadiprivate1
  install-package libqt4-help python-qt4 python-sip python-packagekit
  packagekit gdebi-kde kdepimlibs5 update-manager-kde packagekit-backend-apt
  libqt4-scripttools kdepimlibs-data python-kde4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/279kB of archives.
After this operation, 1,720kB of additional disk space will be used.
Selecting previously deselected package software-center.
(Reading database ... 154790 files and directories currently installed.)
Unpacking software-center (from .../software-center_2.0.7_all.deb) ...
Processing triggers for packagekit-backend-apt ...
Generating mime/codec maps...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-central ...
Processing triggers for python-support ...
Setting up software-center (2.0.7) ...

Processing triggers for python-central ...
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

Attempting to launch remains the same. Hangs on launch for a few moments and all other applications temporarily stop responding, then nothing...

---

### Post by sikander3786 on 2011-02-19
There have been a few bugs with Software Center one of which is listed below. Unfortunately you are being affected with the same one I think and there is no known solution (not in my knowledge at least). Updates might fix it.

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/634324](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/634324)

You might need to switch to some other package manager like Synaptic or apt-get for the time being until your issue is sorted.

Regarding this error,

```
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
```

We need to see the outputs of these commands.

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

### Post by dtaylorjones on 2011-02-19
**cat /etc/apt/sources.list**

```
 # deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner

```**ls -l /etc/apt/sources.list.d**

```
total 20
-rw-r--r-- 1 root root 176 2011-02-12 19:17 google-chrome.list
-rw-r--r-- 1 root root 176 2011-02-12 19:17 google-chrome.list.save
-rw-r--r-- 1 root root 180 2011-02-12 19:17 google-talkplugin.list
-rw-r--r-- 1 root root 180 2011-02-12 19:17 google-talkplugin.list.save
-rw-r--r-- 1 root root 268 2011-02-19 12:37 medibuntu.list
```Another thing I've noticed is my system has become a lot more unstable since this has been going on. I keep needing to force quit things and simple tasks like playing video or starting Firefox often cause a crash which usually results in me having to cold boot the machine. Any way I can increase stability?

Thanks for your help by the way


**EDIT:** Ok the machine is more or less un use-able now. It seems to be getting slower :S. Just opening my home folder causes it to freeze and hang for about a minute. This happens with every action I make (for example clicking on one folder, then another one within it causes a freeze with each action) even typing this text the machine is lagging behind what I type...
I'm running on a Dell XPS M1530 which has more than enough power to run Ubuntu...

---

### Post by dtaylorjones on 2011-02-19
Ok Serious WTF here.
Software centre suddenly started working again. I mean I made NO changes to ANYTHING. Well I installed MPlayer... but I'm pretty sure that had nothing to do with anything and now Software Centre starts and works.

HOWEVER now Transmission (the BitTorrent client) makes everything run at a snails pace when-ever it is running and my copy of the movie "Event Horizon" (.avi) causes a catastrophic crash when-ever I try to play it.

Apart from the occasional "greying out" of applications and stalls everything important seems to be working again... 

I'd mark this thread as "solved" but I don't really feel that we found a solution. Unless the solution is to install MPlayer?..

I don't know, I'm tired and I think I'm starting to hallucinate...

---

### Post by Hello71 on 2011-02-19
At this point, I would start suspecting hardware issues. Try running ```
sudo touch /forcefsck
``` and reboot. This *should* force a disk check on the next reboot. Then, run ```
dmesg
``` and post that here.

---

