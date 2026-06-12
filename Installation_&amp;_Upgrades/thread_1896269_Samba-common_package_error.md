---
title: "Samba-common package error"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by teeth_03 on 2011-12-16
I have a motoroloa atrix phone, and the spiffy laptop dock running a hacked version of the webtop interface (its basically a limited version of debian). Its currently running XFCE4, on top of jaunty pretty much.

Anyway, I need to access windows network shares for work, which is my current issue with the linux on it, and Samba wasn't installed, so I installed it, but i keep getting errors on package samba-common. I have gigolo installed,and when i try to connect to a share, it gives me a "Failed to Mount Windows Share Error". Since it clearly uses samba,im assuming its related to that broken package. I have another computer on the network running xubuntu 11.10 and it connects fine to the same share.

This topic might help clarify, but i dont what read/symlinks are

[http://forum.xda-developers.com/showpost.php?p=19132707&postcount=19](http://forum.xda-developers.com/showpost.php?p=19132707&postcount=19)


```
adas@localhost:/$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtdb1 python-ldb-samba4 python-tdb samba-ldb-tools python-samba
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-common
Suggested packages:
  smbldap-tools ufw
The following NEW packages will be installed:
  samba samba-common
0 upgraded, 2 newly installed, 0 to remove and 129 not upgraded.
Need to get 0B/8412kB of archives.
After this operation, 23.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 
dpkg: serious warning: files list file for package `libmagickcore1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmagickwand1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgd2-noxpm' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gears' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwmf0.2-7' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgraphviz4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libopenexr6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdjvulibre-text' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libilmbase6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblcms1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `imagemagick' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdjvulibre21' missing, assuming package has no files currently installed.
[59068]("tel:59068") files and directories currently installed.)
Unpacking samba-common (from .../samba-common_2%3a3.3.2-1ubuntu3.6_armel.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_2%3a3.3.2-1ubuntu3.6_armel.deb) ...
Setting up samba-common (2:3.3.2-1ubuntu3.6) ...
readlink: invalid option -- 'q'
BusyBox v1.10.2 (2010-10-25 17:12:51 PDT) multi-call binary

Usage: readlink [-f] FILE

Display the value of a symlink

Options:
    -f    Canonicalize by following all symlinks

ucf: Unable to determine The new file
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3.6); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba-common
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by teeth_03 on 2011-12-16
*bump*

anyone got any advice or know where I could look for a solution? Thank you

---

