---
title: "lucid package install and config problem"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by svaens on 2010-03-12
Hi all, 

I thought i'd try and do some testing for lucid, get it going on a new partition on my computer, and see what problems exist.

I have a problem now while trying to install the adium-theme-ubuntu package (which comes with ubuntu-artwork* and ubuntu-desktop*.

The problem turned up while doing an update. I clicked something I shouldn't have during the update was doing its configuring, and I froze the system. No way to exit but to hard-shutdown, restart. 
Then ubuntu wouldn't start without going to recovery mode and cleaning it up. However, not everything cleaned up. 

And I can only guess it is because of the interrupted update, but maybe not. I don't know. I also don't know how to recover. 

Here is what I get. I have tried apt-get install --fix-broken and all that. a purge and re-install... hasn't fixed it. 

But i'm not very expert on linux yet. 

Here's some console to show you what is happening;


```

sean@svUbuntuX2:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up adium-theme-ubuntu (0.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing adium-theme-ubuntu (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of ubuntu-artwork:
 ubuntu-artwork depends on adium-theme-ubuntu; however:
  Package adium-theme-ubuntu is not configured yet.
dpkg: error processing ubuntu-artwork (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on ubuntu-artwork; however:
  Package ubuntu-artwork is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                   Errors were encountered while processing:
 adium-theme-ubuntu
 ubuntu-artwork
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


and after trying a purge

> 

sean@svUbuntuX2:~$ sudo apt-get remove adium-theme-ubuntu --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adium-theme-ubuntu* ubuntu-artwork* ubuntu-desktop*
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
3 not fully installed or removed.
After this operation, 565kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 124736 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing ubuntu-artwork ...
Purging configuration files for ubuntu-artwork ...
Removing adium-theme-ubuntu ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing adium-theme-ubuntu (--purge):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 adium-theme-ubuntu
E: Sub-process /usr/bin/dpkg returned an error code (1)
sean@svUbuntuX2:~$ sudo apt-get install adium-theme-ubuntu 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
adium-theme-ubuntu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up adium-theme-ubuntu (0.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing adium-theme-ubuntu (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 adium-theme-ubuntu
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

