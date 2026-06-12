---
title: "Virtual Box - Kernel driver not installed (rc=-1908)"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by nemesis855 on 2013-06-01
My first post here folks, so please excuse my "newbieness".

Taking yet another stab at linux in the form of lubuntu 12.10 (currently in about 6 months). I was able to install virtualbox awhile back without incident. Recently, I installed some "kernal header" upgrades through "Software Updater". After these upgrades, I was able to open Virtual Box, but trying to open my MS-DOS 6.22 virtual box produced the following error:

"Kernel driver not installed (rc=-1908)


The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

I ran the above command as indicated using 'sudo' in a command shell and got the following:

"notmyrealuserid:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found"

My next step was to uninstall virtualbox (after much "googleling") and try again. I succeeded in installing and reinstalled virtualbox. 

I restarted VB and created an entry for another virtual MS-DOS machine. I started it up and got the same "Kernal driver not installed" error. What follows below is the result of my second installation of virtual box. I apologize for the length, but I'm hoping the more info I provide, the better chance someone will have of pointing me in the right direction. It looks like I have a lot of dependency errors, so I'm guessing a number of items are not correctly installed

Any ideas anyone has would be greatly apprciated.
```

---------------------------------------------------------------------------------------------------------------------------------------------------
notmyrealuserid:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  hyphen-en-us linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
  mythes-en-au openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  virtualbox-dkms virtualbox-qt
Suggested packages:
  virtualbox-guest-additions-iso vde2
The following NEW packages will be installed:
  virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0 B/17.6 MB of archives.
After this operation, 69.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
Selecting previously unselected package virtualbox.
(Reading database ... 385847 files and directories currently installed.)
Unpacking virtualbox (from .../virtualbox_4.1.18-dfsg-1ubuntu1.2_i386.deb) ...
Selecting previously unselected package virtualbox-dkms.
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.18-dfsg-1ubuntu1.2_all.deb) ...
Selecting previously unselected package virtualbox-qt.
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.18-dfsg-1ubuntu1.2_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Setting up libssl1.0.0:i386 (1.0.1c-3ubuntu2.4) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing libssl1.0.0:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apparmor (2.8.0-0ubuntu5.1) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up cups (1.6.1-0ubuntu11.4) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up rsyslog (5.8.6-1ubuntu9.2) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up man-db (2.6.3-1) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.1); however:
  Package libssl1.0.0:i386 is not configured yet.

dpkg: error processing openssl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up bridge-utils (1.5-4ubuntu2) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing bridge-utils (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up flashplugin-installer (11.2.202.285ubuntu0.12.10.1) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libafflib0:
 libafflib0 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.

dpkg: error processing libafflib0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libruby1.8:
 libruby1.8 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.

dpkg: error processing libruby1.8 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libvirt-bin:
 libvirt-bin depends on bridge-utils; however:
  Package bridge-utils is not configured yet.

dpkg: error processing libvirt-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ruby1.8:
 ruby1.8 depends on libruby1.8 (= 1.8.7.358-4ubuntu0.2); however:
  Package libruby1.8 is not configured yet.

dpkg: error processing ruby1.8 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ruby1.8-dev:
 ruby1.8-dev depends on libruby1.8 (= 1.8.7.358-4ubuntu0.2); however:
  Package libruby1.8 is not configured yet.

dpkg: error processing ruby1.8-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of rubygems:
 rubygems depends on ruby1.8; however:
  Package ruby1.8 is not configured yet.

dpkg: error processing rubygems (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of vagrant:
 vagrant depends on rubygems (>= 1.3.6); however:
  Package rubygems is not configured yet.

dpkg: error processing vagrant (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of xmount:
 xmount depends on libafflib0; however:
  Package libafflib0 is not configured yet.

dpkg: error processing xmount (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up cups-bsd (1.6.1-0ubuntu11.4) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing cups-bsd (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up nullmailer (1:1.11-2) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing nullmailer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:i386 is not configured yet.

dpkg: error processing virtualbox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of virtualbox-dkms:
 virtualbox-dkms depends on virtualbox (>= 4.1.18-dfsg-1ubuntu1.2); however:
  Package virtualbox is not configured yet.

dpkg: error processing virtualbox-dkms (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of virtualbox-qt:
 virtualbox-qt depends on virtualbox (= 4.1.18-dfsg-1ubuntu1.2); however:
  Package virtualbox is not configured yet.

dpkg: error processing virtualbox-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libssl1.0.0:i386
 apparmor
 cups
 rsyslog
 man-db
 openssl
 bridge-utils
 flashplugin-installer
 libafflib0
 libruby1.8
 libvirt-bin
 ruby1.8
 ruby1.8-dev
 rubygems
 vagrant
 xmount
 cups-bsd
 nullmailer
 virtualbox
 virtualbox-dkms
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ahallubuntu on 2013-06-01
~

---

### Post by newb85 on 2013-06-02
Yes, that solution has fixed it for me several times.  That's the problem.  I've had to apply this solution with *every* kernel update.  I'm not familiar with the inner workings of dependencies, but it seems like something is missing here.

---

### Post by nemesis855 on 2013-06-02
I've seen this given as an "answer" to this problem. Any ideas as to what command is "not found"?

"notmyrealid:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found"

---

