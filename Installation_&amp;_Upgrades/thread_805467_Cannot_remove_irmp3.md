---
title: "Cannot remove irmp3"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by enoughsaid05 on 2008-05-24
Hi all,

I wanted to see what irmp3 was so I went to install, but then when I want to remove irmp3, this is what I got:

user@user-laptop:~$ sudo aptitude remove irmp3
[sudo] password for weiguo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  irmp3 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 410kB will be freed.
Writing extended state information... Done
(Reading database ... 159865 files and directories currently installed.)
Removing irmp3 ...
Stopping irmp3: invoke-rc.d: initscript irmp3, action "stop" failed.
dpkg: error processing irmp3 (--remove):
 subprocess pre-removal script returned error exit status 1
Starting irmp3: irmp3.
Errors were encountered while processing:
 irmp3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
weiguo@weiguo-laptop:~$ sudo aptitude remove irmp3 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  irmp3 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 410kB will be freed.
Writing extended state information... Done
(Reading database ... 159865 files and directories currently installed.)
Removing irmp3 ...
Stopping irmp3: invoke-rc.d: initscript irmp3, action "stop" failed.
dpkg: error processing irmp3 (--remove):
 subprocess pre-removal script returned error exit status 1
Starting irmp3: irmp3.
Errors were encountered while processing:
 irmp3
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
weiguo@weiguo-laptop:~$

How do I resolve the problem??
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by iaculallad on 2008-05-24
Seems like a broken uninstall script. You could remove your irmp3 but with a long-cut method.

Try doing this:

sudo slocate -u
slocate irmp3

and whatever appears, try deleting them manually :-)

---

