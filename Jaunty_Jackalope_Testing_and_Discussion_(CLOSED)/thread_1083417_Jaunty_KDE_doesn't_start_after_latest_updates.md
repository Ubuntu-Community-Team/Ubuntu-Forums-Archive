---
title: "Jaunty KDE doesn't start after latest updates"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cesera on 2009-02-28
After this mornings updates to Jaunty (253 of them) my kde doesn't start anymore. When I log in the console (Alt+F1) I get lots of the following error message:
 
> Couldn't open /dev/null: Permission denied
 
When I run apt-get I get the following:
 
 
> Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be upgraded:
  xserver-xorg
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
253 not fully installed or removed.
Need to get 0B/194kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Segmentation fault (core dumped)
(Reading database ... 155935 files and directories currently installed.)
Preparing to replace xserver-xorg 1:7.4~5ubuntu12 (using .../xserver-xorg_1%3a7.4~5ubuntu13_amd64.deb) ...
dpkg: warning - old pre-removal script killed by signal (Segmentation fault), core dumped
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg_1%3a7.4~5ubuntu13_amd64.deb (--unpack):
 subprocess new pre-removal script killed by signal (Segmentation fault), core dumped
dpkg: error while cleaning up:
 subprocess post-installation script killed by signal (Segmentation fault), core dumped
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg_1%3a7.4~5ubuntu13_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cesera on 2009-03-07
I gave up waiting and installed Alpha 5 from scratch.

---

