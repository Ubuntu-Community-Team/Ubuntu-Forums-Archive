---
title: "gnome-system-tools not fully installed"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by rciemins on 2012-02-29
Hello... Fresh Ubuntu 10.4. Installed all updates, but one thing failed... Now I can't get rid of this error. Any ideas?


**sabux@sabux-laptop:~$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnome-system-tools (2.30.0-0ubuntu3) ...
Warning: /usr/share/gconf/schemas/gnome-system-tools.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gnome-system-tools (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

**sabux@sabux-laptop:~$ sudo apt-get purge gnome-system-tools**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-system-tools*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9,253kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127625 files and directories currently installed.)
Removing gnome-system-tools ...
Warning: /usr/share/gconf/schemas/gnome-system-tools.schemas could not be found.
Usage: gconf-schemas --[un]register file1.schemas [file2.schemas [...]]

gconf-schemas: error: You need at least a file to (un)register.
dpkg: error processing gnome-system-tools (--purge):
 subprocess installed pre-removal script returned error exit status 2
Errors were encountered while processing:
 gnome-system-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
sabux@sabux-laptop:~$

---

### Post by rciemins on 2012-02-29
This helped.
[http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/](http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/)

---

