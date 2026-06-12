---
title: "Having problems in installing anything"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by shubham.joy on 2011-02-12
Hello.
my bluetooth was not working. It says **Please verify that the "Personal File Sharing" program is correctly installed.** So I removed it and tried to install some softwares that I got when I searched bluetooth in Synaptic package manager.
Some softwares installed but one of the software hanged so I had to reboot in between.

After I restarted my system and now whenever I am trying to install anything using apt-get I get the following messages:

```

shubhu@Shubhu-Roxxx:~$ sudo apt-get install ssh
[sudo] password for shubhu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ssh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up dahdi-dkms (1:2.2.1+dfsg-1ubuntu3) ...
Removing old dahdi-2.2.1+dfsg-1ubuntu3 DKMS files...

------------------------------
Deleting module version: 2.2.1+dfsg-1ubuntu3
completely from the DKMS tree.
------------------------------
Done.
Loading new dahdi-2.2.1+dfsg-1ubuntu3 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-26-generic
Building for architecture x86_64
Building initial module for 2.6.35-26-generic

```It hangs here for some time and then the following is displayed
```

Error!  Build of dahdi_vpmadt032_loader.ko failed for: 2.6.35-26-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/dahdi/2.2.1+dfsg-1ubuntu3/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/dahdi-dkms.0.crash'
dpkg: error processing dahdi-dkms (--configure):
 subprocess installed post-installation script returned error exit status 7
dpkg: dependency problems prevent configuration of dahdi-linux:
 dahdi-linux depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dahdi:
 dahdi depends on dahdi-linux; however:
  Package dahdi-linux is not configured yet.
 dahdi depends on dahdi-dkms | dahdi-source; however:
  Package dahdi-dkms is not configured yet.
  Package dahdi-source is not installed.
dpkg: error processing dahdi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopenr2-3:
 libopenr2-3 depends on dahdi; however:
  Package dahdi is not configured yet.
dpkg: error processing libopenr2-3 (--configure):
 dependency pNo apport report written because the error message indicates its a followup error from a previous failure.
                                       No apport report written because the error message indicates its a followup error from a previous failure.
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           roblems - leaving unconfigured
dpkg: dependency problems prevent configuration of asterisk:
 asterisk depends on libopenr2-3; however:
  Package libopenr2-3 is not configured yet.
 asterisk depends on dahdi; however:
  Package dahdi is not configured yet.
dpkg: error processing asterisk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asterisk-mobile:
 asterisk-mobile depends on asterisk-1.6.2; however:
  Package asterisk-1.6.2 is not installed.
  Package asterisk which provides asterisk-1.6.2 is not configured yet.
dpkg: error processing asterisk-mobile (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dahdi-dkms
 dahdi-linux
 dahdi
 libopenr2-3
 asterisk
 asterisk-mobile
E: Sub-process /usr/bin/dpkg returned an error code (1)
shubhu@Shubhu-Roxxx:~$ 

```Everytime any software I try it shows the same thing. How can I remove this problem??
Also if any suggestion on how to make my bluetooth work are also welcome. Thanks

---

### Post by shubham.joy on 2011-02-12
Looks like I have solved it. Just uninstalled dahdi from synaptics package manager.
By the way any suggestion on how to solve my Bluetooth problem?

---

