---
title: "Need help to completely remove flgrx after a disaster install"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by readycarpenter on 2011-11-14
I have exactly the same issue as this guy. [http://kubuntuforums.net/forums/index.php?topic=3117855.msg269943#msg269943](http://kubuntuforums.net/forums/index.php?topic=3117855.msg269943#msg269943)

I am running ubuntu 11.10, ati aditional drivers were working fine until I installed the ati drivers from source, then I rebooted got to the login screen and then a black screen, I have tried everything this guy did and no luck.

------------------
hdavy2002@Davy:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libzrtpcpp-1.4-0 libccrtp1-1.7-0 libccgnu2-1.7-0 libqt3-mt libboost-regex1.42.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/41.3 MB of archives.
After this operation, 127 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158370 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb                                          
E: Sub-process /usr/bin/dpkg returned an error code (1)  

I had previously build packages using

$ sudo sh ./ati-driver-installer-11-7-x86.x86_64.run --buildpkg Ubuntu/natty

then today, I tried again

hdavy2002@Davy:/media/windata/linux/Softwares$ ls
ati-driver-installer-11-6-x86.x86_64.run  fglrx-installer_8.861-0ubuntu1_amd64.changes
Fedora-15-x86_64-Live-Desktop.iso         openSUSE-11.4-Addon-NonOss-BiArch-i586-x86_64.iso
fglrx_8.840-0ubuntu4_amd64.deb            openSUSE-KDE-LiveCD-Build0072-i686.iso
fglrx_8.861-0ubuntu1_amd64.deb            rtl8192efirmware.zip
fglrx-amdcccle_8.861-0ubuntu1_amd64.deb   rtl8192se_linux_2.6.0010.1020.2009_64bit
fglrx-dev_8.861-0ubuntu1_amd64.deb        supertuxkart-0.7.2a-linux-glibc2.12-x86-64.tar.bz2

hdavy2002@Davy:/media/windata/linux/Softwares$ sudo dpkg -i *.deb
(Reading database ... 158418 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.840-0ubuntu4_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing fglrx_8.840-0ubuntu4_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Unpacking fglrx (from fglrx_8.861-0ubuntu1_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing fglrx_8.861-0ubuntu1_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace fglrx-amdcccle 2:8.850-0ubuntu1~xup2~natty (using fglrx-amdcccle_8.861-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.861-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx_8.840-0ubuntu4_amd64.deb
 fglrx_8.861-0ubuntu1_amd64.deb
 fglrx-amdcccle
 fglrx-dev
hdavy2002@Davy:/media/windata/linux/Softwares$ 
------------------

---

### Post by MAFoElffen on 2011-11-15
> **readycarpenter said:**
> I have exactly the same issue as this guy. [http://kubuntuforums.net/forums/index.php?topic=3117855.msg269943#msg269943](http://kubuntuforums.net/forums/index.php?topic=3117855.msg269943#msg269943)

I am running ubuntu 11.10, ati aditional drivers were working fine until I installed the ati drivers from source, then I rebooted got to the login screen and then a black screen, I have tried everything this guy did and no luck.

------------------
hdavy2002@Davy:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libzrtpcpp-1.4-0 libccrtp1-1.7-0 libccgnu2-1.7-0 libqt3-mt libboost-regex1.42.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/41.3 MB of archives.
After this operation, 127 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 158370 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.850-0ubuntu1~xup2~natty_amd64.deb                                          
E: Sub-process /usr/bin/dpkg returned an error code (1)  

I had previously build packages using

$ sudo sh ./ati-driver-installer-11-7-x86.x86_64.run --buildpkg Ubuntu/natty

then today, I tried again

hdavy2002@Davy:/media/windata/linux/Softwares$ ls
ati-driver-installer-11-6-x86.x86_64.run  fglrx-installer_8.861-0ubuntu1_amd64.changes
Fedora-15-x86_64-Live-Desktop.iso         openSUSE-11.4-Addon-NonOss-BiArch-i586-x86_64.iso
fglrx_8.840-0ubuntu4_amd64.deb            openSUSE-KDE-LiveCD-Build0072-i686.iso
fglrx_8.861-0ubuntu1_amd64.deb            rtl8192efirmware.zip
fglrx-amdcccle_8.861-0ubuntu1_amd64.deb   rtl8192se_linux_2.6.0010.1020.2009_64bit
fglrx-dev_8.861-0ubuntu1_amd64.deb        supertuxkart-0.7.2a-linux-glibc2.12-x86-64.tar.bz2

hdavy2002@Davy:/media/windata/linux/Softwares$ sudo dpkg -i *.deb
(Reading database ... 158418 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.840-0ubuntu4_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing fglrx_8.840-0ubuntu4_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Unpacking fglrx (from fglrx_8.861-0ubuntu1_amd64.deb) ...
/usr/share/ati/fglrx-uninstall.sh: 32: cannot create /etc/ati/fglrx-uninstall.log: Directory nonexistent

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the force option
 re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing fglrx_8.861-0ubuntu1_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace fglrx-amdcccle 2:8.850-0ubuntu1~xup2~natty (using fglrx-amdcccle_8.861-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.861-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx_8.840-0ubuntu4_amd64.deb
 fglrx_8.861-0ubuntu1_amd64.deb
 fglrx-amdcccle
 fglrx-dev
hdavy2002@Davy:/media/windata/linux/Softwares$ 
------------------
After running 
```

sudo sh /usr/share/ati/fglrx-uninstall.sh

```
Try steps 3 and 4 here:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")** 

So both of you insalled different type of drivers without removing previous drivers?  And you know that his instruction had "natty" in the switch for the shell file, where you need that mod'ed for what you are running right? You are running 10.04 right?  Look again further down in the instructions on my link... 
[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by BillyBoa on 2011-11-15
If the above solutions don't work you can delete it through Synaptic. Also you can check there for broken packages.

---

