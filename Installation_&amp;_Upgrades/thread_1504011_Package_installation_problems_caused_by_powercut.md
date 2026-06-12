---
title: "Package installation problems caused by powercut"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by SteelSlasher on 2010-06-07
Hi, I was installing rosegarden the other day and during the installation of other dependencies there was a power cut (it wasnt expected nor are power cuts common in the UK)

for some reason rosegarden works completely fine but i now have 7 or so partially installed packages which cause the attempt to install anything fail.

Just to try and display what I mean, i just tried to update gedit but instead it fails because it tries to uninstall the partially installed packages which for some reason does not work.

It seems that some files do exist so it must think that some packages are installed when no files exist

i also get a bright red exclamation mark in the corner of the screen, i assume it is related to this error
> sameh@sameh-desktop:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit is already the newest version.
The following packages will be REMOVED
  jackd libffado2 liblo7 liblrdf0 libxml++2.6-2 texinfo
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 5,534kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 185493 files and directories currently installed.)
Removing jackd ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing jackd (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing libffado2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libffado2 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing liblo7 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liblo7 (--remove):
 subprocess installed post-removal script returned error exit status 2
Removing liblrdf0 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liblrdf0 (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Removing libxml++2.6-2 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing libxml++2.6-2 (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Removing texinfo ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing texinfo (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 jackd
 libffado2
 liblo7
 liblrdf0
 libxml++2.6-2
 texinfo
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by boonenoob on 2010-06-07
do this in terminal
```
sudo apt-get remove jackd libffado2 liblo7   liblrdf0 libxml++2.6-2 texinfo
```then if you want to reinstall those do this:
```
sudo apt-get install jackd libffado2 liblo7   liblrdf0 libxml++2.6-2 texinfo
```


*EDIT* if this doesn't work copy/paste the output of:
```
sudo apt-get check
```
in a post here

---

### Post by SteelSlasher on 2010-06-08
Those commands solved most of the problems but some more have appeared
> sameh@sameh-desktop:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree        
Reading state information... Done
gedit is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up guile-1.8 (1.8.7+1-3ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing guile-1.8 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up tex-common (2.06) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 guile-1.8
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)


sameh@sameh-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done


---

