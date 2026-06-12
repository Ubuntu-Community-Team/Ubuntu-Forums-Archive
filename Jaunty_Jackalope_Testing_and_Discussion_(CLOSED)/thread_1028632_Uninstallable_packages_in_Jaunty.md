---
title: "Uninstallable packages in Jaunty"
date: 2009-01-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TDFlanders on 2009-01-02
uml-utilities
user-mode-linux
acpi-dbgsym
libseda-java
azureus
vuze
gscan2pdf
libsane-perl

Do I need to file a big against all of these?

Cheers,

Thomas

---

### Post by TDFlanders on 2009-01-02
I meant to file a bug off course ....

---

### Post by danf_1979 on 2009-01-02
What do you mean by uninstallable? could you provide some apt-get or aptitude's console output?

---

### Post by ronacc on 2009-01-02
libseda-java is the blocker ,it is not in the jaunty repo , you can get it here .
[https://launchpad.net/ubuntu/jaunty/i386/libseda-java/3.0-3 ](https://launchpad.net/ubuntu/jaunty/i386/libseda-java/3.0-3 )

---

### Post by TDFlanders on 2009-01-03
root@thomas-laptop:/home/thomas# apt-get install acpi-dbgsym
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  acpi-dbgsym: Depends: acpi (= 1.1-1ubuntu1) but 1.2-1ubuntu1 is to be installed
E: Broken packages
root@thomas-laptop:/home/thomas# apt-get install gscan2pdf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gscan2pdf: Depends: libsane-perl but it is not installable
E: Broken packages
root@thomas-laptop:/home/thomas# apt-get install libsane-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsane-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsane-perl has no installation candidate
root@thomas-laptop:/home/thomas# linux
The program 'linux' is currently not installed.  You can install it by typing:
apt-get install user-mode-linux
bash: linux: command not found
root@thomas-laptop:/home/thomas# apt-get install user-mode-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  uml-utilities
Suggested packages:
  rootstrap user-mode-linux-doc slirp linux-patch-skas
The following NEW packages will be installed
  uml-utilities user-mode-linux
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/41.9MB of archives.
After this operation, 107MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package uml-utilities.
(Reading database ... 350143 files and directories currently installed.)
Unpacking uml-utilities (from .../uml-utilities_20070815-1.1ubuntu1_i386.deb) ...
Selecting previously deselected package user-mode-linux.
Unpacking user-mode-linux (from .../user-mode-linux_2.6.22-2um-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up uml-utilities (20070815-1.1ubuntu1) ...
 * Starting User-mode networking switch uml_switch                               * /usr/bin/uml_switch never created control socket /var/run/uml-utilities/uml_switch.ctl
                                                                         [fail]
invoke-rc.d: initscript uml-utilities, action "start" failed.
dpkg: error processing uml-utilities (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of user-mode-linux:
 user-mode-linux depends on uml-utilities (>= 20040406-1); however:
  Package uml-utilities is not configured yet.
dpkg: error processing user-mode-linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 uml-utilities
 user-mode-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@thomas-laptop:/home/thomas# apt-get install uml-utilities
Reading package lists... Done
Building dependency tree       
Reading state information... Done
uml-utilities is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up uml-utilities (20070815-1.1ubuntu1) ...
 * Starting User-mode networking switch uml_switch                               * /usr/bin/uml_switch never created control socket /var/run/uml-utilities/uml_switch.ctl
                                                                         [fail]
invoke-rc.d: initscript uml-utilities, action "start" failed.
dpkg: error processing uml-utilities (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of user-mode-linux:
 user-mode-linux depends on uml-utilities (>= 20040406-1); however:
  Package uml-utilities is not configured yet.
dpkg: error processing user-mode-linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 uml-utilities
 user-mode-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@thomas-laptop:/home/thomas# apt-get install libseda-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libseda-java is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libseda-java has no installation candidate
root@thomas-laptop:/home/thomas# apt-get install vuze
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  vuze: Depends: azureus but it is not going to be installed
E: Broken packages
root@thomas-laptop:/home/thomas# apt-get install azureus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  azureus: Depends: libseda-java but it is not installable
E: Broken packages
root@thomas-laptop:/home/thomas#

---

### Post by TDFlanders on 2009-01-03
Hi guys,

thanks for the help.

What I really meant:

Do I need to file a bug against every individual package or will 1 metabug do, or all related dependencies together?

Anyway, thanks again and I will now try the libseda-java workaround as posted here.

Cheers,

Thomas

---

### Post by TDFlanders on 2009-01-03
root@thomas-laptop:/home/thomas# apt-get install rootstrap user-mode-linux-doc slirp linux-patch-skas
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-patch-skas is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-patch-skas has no installation candidate

---

### Post by ronacc on 2009-01-03
I didn't try ulm , but libseda-java from the link I cited did let me install azureus and was also blocking vuze .

---

### Post by danf_1979 on 2009-01-04
> **TDFlanders said:**
> 
Do I need to file a bug against every individual package or will 1 metabug do, or all related dependencies together?


One bug report per package seems the best thing to do.

---

### Post by TDFlanders on 2009-01-04
root@thomas-laptop:/home/thomas# dpkg-reconfigure flashplugin-nonfree
Configuring flashplugin-nonfree
-------------------------------

Have you already downloaded the .tar.gz package from Adobe? If so, please enter 
the directory you downloaded it into. Do not include the filename here. If you 
have not already downloaded it, leave this blank and the package will be 
downloaded automatically.

Location to the local file: 


The Adobe flash plugin is to be downloaded from [www.adobe.com](www.adobe.com).  This can be done
automatically now.  The distribution license of the Adobe flash plugin is 
available at [www.adobe.com](www.adobe.com).

Do you accept the license and do you want to download the flash plugin now? yes


Downloading...
--2009-01-04 18:44:30--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.15.3.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.15.3.orig.tar.gz)
Resolving archive.canonical.com... failed: Name or service not known.
wget: unable to resolve host address `archive.canonical.com'
download failed
The Flash plugin is NOT installed.
root@thomas-laptop:/home/thomas# dpkg-reconfigure flashplugin-nonfree
Configuring flashplugin-nonfree
-------------------------------

Have you already downloaded the .tar.gz package from Adobe? If so, please enter 
the directory you downloaded it into. Do not include the filename here. If you 
have not already downloaded it, leave this blank and the package will be 
downloaded automatically.

Location to the local file: /var/cache/flashplugin-nonfree


download or license refused
The Flash plugin is NOT installed.
root@thomas-laptop:/home/thomas#

---

### Post by TDFlanders on 2009-01-05
Hi there danf,

thanks for the tip, I will post single bugs for every package.

I was able to do your work around ronacc. Thanks for the website. So far I have:

root@thomas-laptop:/home/thomas# apt-cache policy uml-utilities user-mode-linux libseda-java libsane-perl gscan2pdf azureus vuze acpi-dbgsym linux-backports-modules-jaunty-generic flashplugin-nonfree linux-patch-skas
uml-utilities:
  Installed: 20070815-1.1ubuntu1
  Candidate: 20070815-1.1ubuntu1
  Version table:
 *** 20070815-1.1ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
        100 /var/lib/dpkg/status
user-mode-linux:
  Installed: 2.6.22-2um-0ubuntu2
  Candidate: 2.6.22-2um-0ubuntu2
  Version table:
 *** 2.6.22-2um-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
        100 /var/lib/dpkg/status
libseda-java:
  Installed: 3.0-3
  Candidate: 3.0-3
  Version table:
 *** 3.0-3 0
        100 /var/lib/dpkg/status
libsane-perl:
  Installed: (none)
  Candidate: (none)
  Version table:
gscan2pdf:
  Installed: (none)
  Candidate: 0.9.27-1
  Version table:
     0.9.27-1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
azureus:
  Installed: 3.1.1.0-3ubuntu3
  Candidate: 3.1.1.0-3ubuntu3
  Version table:
 *** 3.1.1.0-3ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
        100 /var/lib/dpkg/status
vuze:
  Installed: 3.1.1.0-3ubuntu3
  Candidate: 3.1.1.0-3ubuntu3
  Version table:
 *** 3.1.1.0-3ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
        100 /var/lib/dpkg/status
acpi-dbgsym:
  Installed: (none)
  Candidate: 1.1-1ubuntu1
  Version table:
     1.1-1ubuntu1 0
        500 [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) intrepid/main Packages
linux-backports-modules-jaunty-generic:
  Installed: (none)
  Candidate: 2.6.28.4.4
  Version table:
     2.6.28.4.4 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
flashplugin-nonfree:
  Installed: 10.0.15.3ubuntu2
  Candidate: 10.0.15.3ubuntu2
  Version table:
 *** 10.0.15.3ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
        100 /var/lib/dpkg/status
linux-patch-skas:
  Installed: (none)
  Candidate: (none)
  Version table:
root@thomas-laptop:/home/thomas#

---

