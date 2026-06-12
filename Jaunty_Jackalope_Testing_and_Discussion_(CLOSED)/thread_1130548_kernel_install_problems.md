---
title: "kernel install problems"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Woody1987 on 2009-04-19
For about a week now i have been unable to upgrade my kernel. i get dependency problems. I ran sudo apt-get install -f and i get 

> matt@matt-desktop:~$ sudo apt-get install -f
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  linux-image
The following NEW packages will be installed
  linux-image
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 3370B of archives.
After this operation, 32.8kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main linux-image 2.6.28.11.15 [3370B]
Fetched 3370B in 0s (70.5kB/s)    
Selecting previously deselected package linux-image.
(Reading database ... 165785 files and directories currently installed.)
Unpacking linux-image (from .../linux-image_2.6.28.11.15_amd64.deb) ...
Setting up linux-image-2.6.28-11-generic (2.6.28-11.42) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.28.11.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-11-generic:
 linux-restricted-modules-2.6.28-11-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-11-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because the error message indicates its a followup error from a previous failure.
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  uration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-11-generic; however:
  Package linux-restricted-modules-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 2.6.28.11.15); however:
  Package linux-image is not configured yet.
 linux depends on linux-restricted-modules (= 2.6.28.11.15); however:
  Package linux-restricted-modules is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.11.15); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.11.15); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-11-generic
 linux-image-generic
 linux-image
 linux-restricted-modules-2.6.28-11-generic
 linux-restricted-modules-generic
 linux-restricted-modules
 linux
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have installed the 2.6.30 rc2 kernel and it is working, but i would much rather run the stable supported kernel that comes with jaunty. Any help appreciated

---

### Post by Woody1987 on 2009-04-20
bump

---

### Post by Woody1987 on 2009-04-21
anyone?

---

### Post by HankB on 2009-04-21
> **Woody1987 said:**
> anyone?

That's me! ;)

disk space?

Have you tried "sudo dpkg --configure -a"

HTH,
hank

---

### Post by stuart264 on 2009-04-22
I have the same problem and sudo dpkg --configure -a didnt do a thing

---

### Post by xebian on 2009-04-22
dpkg -i --force-all /var/cache/apt/archives/linux* will solve your problem.

Normally those linux or linux-image or linux-generic are redundant, and if not packaged properly will cause all your dependency issues.

---

