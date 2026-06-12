---
title: "Somehow I cant update"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by rubenhkoster on 2012-12-30
Tried alot of things but suddenly I can not install any updates anymore through terminal..
My update manager wont start up anymore, what to do?
This says my terminal after update and upgrade commands;
```
ruben@ruben:~$ sudo apt-get update 
[sudo] password for ruben: 
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease 
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                     
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports InRelease         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal Release.gpg
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates Release.gpg          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/main Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/multiverse Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/restricted i386 Packages    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/universe i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/multiverse i386 Packages    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/universe Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/multiverse Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/main i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/universe Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/main Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/restricted Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/universe Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/multiverse Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/main i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/universe Translation-en
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Reading package lists... Done
ruben@ruben:~$ sudo su
root@ruben:/home/ruben# j
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
root@ruben:/home/ruben# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 apport : Depends: python3-apport (>= 2.6.1-0ubuntu9) but 2.6.1-0ubuntu3 is installed
 apport-gtk : Depends: python3-apport (>= 2.6.1-0ubuntu9) but 2.6.1-0ubuntu3 is installed
 ubuntu-release-upgrader-core : Depends: python3-distupgrade (= 1:0.190.4) but 1:0.190.1 is installed
 ubuntu-release-upgrader-gtk : Depends: python3-distupgrade (= 1:0.190.4) but 1:0.190.1 is installed
E: Unmet dependencies. Try using -f.
root@ruben:/home/ruben# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python3-apport python3-distupgrade
Suggested packages:
  python3-launchpadlib
The following packages will be upgraded:
  python3-apport python3-distupgrade
2 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
141 not fully installed or removed.
Need to get 0 B/1,568 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: warning: files list file for package 'update-manager' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-manager-core' missing; assuming package has no files currently installed
(Reading database ... 151875 files and directories currently installed.)
Preparing to replace python3-distupgrade 1:0.190.1 (using .../python3-distupgrade_1%3a0.190.4_all.deb) ...
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 134
dpkg: trying script from the new package instead ...
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: error processing /var/cache/apt/archives/python3-distupgrade_1%3a0.190.4_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 134
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 134
Preparing to replace python3-apport 2.6.1-0ubuntu3 (using .../python3-apport_2.6.1-0ubuntu9_all.deb) ...
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: warning: subprocess old pre-removal script returned error exit status 134
dpkg: trying script from the new package instead ...
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: error processing /var/cache/apt/archives/python3-apport_2.6.1-0ubuntu9_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 134
Fatal Python error: Py_Initialize: Unable to get the locale encoding
EOFError: EOF read where not expected
Aborted (core dumped)
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 134
Errors were encountered while processing:
 /var/cache/apt/archives/python3-distupgrade_1%3a0.190.4_all.deb
 /var/cache/apt/archives/python3-apport_2.6.1-0ubuntu9_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Frogs Hair on 2012-12-30
Try the following.

```
sudo rm -r /var/lib/apt/lists/*
``````
sudo apt-get update
```

---

