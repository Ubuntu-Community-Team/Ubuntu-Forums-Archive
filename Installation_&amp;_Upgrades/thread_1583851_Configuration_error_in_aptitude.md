---
title: "Configuration error in aptitude"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by heyson-alice on 2010-09-28
Hi,

I think I messed up one of my packages, and now it wants to configure itself. If I execute aptitude update, upgrade, install or remove it does what it should do - but it always tries and fails on the configuration of this application.

The concerned package is "icecast2". I do not want it anymore. There is no script for it in /etc/init.d/ and the configuration file is empty.

When I try any aptitude command (in this example "sudo aptitude remove subversion"), I see this:
> martin@POLAPC-04:~$ sudo aptitude remove subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  libsvn1{u} subversion 
The following partially installed packages will be configured:
  icecast2 
0 packages upgraded, 0 newly installed, 2 to remove and 203 not upgraded.
Need to get 0B of archives. After unpacking 6,570kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 198690 files and directories currently installed.)
Removing subversion ...
Removing libsvn1 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up icecast2 (2.3.2-5ubuntu1) ...
update-rc.d: warning: /etc/init.d/icecast2 missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Starting icecast2: Starting icecast2
Detaching from the console
/etc/icecast2/icecast.xml:1: parser error : Document is empty

^
/etc/icecast2/icecast.xml:1: parser error : Start tag expected, '<' not found

^
FATAL: error parsing config file (/etc/icecast2/icecast.xml)
XML config parsing error
start-stop-daemon: stat /usr/bin/ices2: No such file or directory (No such file or directory)
invoke-rc.d: initscript icecast2, action "start" failed.
dpkg: error processing icecast2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icecast2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

It removes/installs/upgrades succesfully, but it does not configure. In fact, I do not want it to configure, I only want it to leave my computer alone.

If I upgrade the system with the upgrade manager in Kubuntu, it upgrades but I get a dialog box abount an error. I think it's really annoying and pointless - since it worked.

Grateful for replies.

---

### Post by andrewthomas on 2010-09-29
post the output of ```
sudo aptitude reinstall icecast2 && sudo aptitude remove icecast2
```

---

