---
title: "cannot install/update/remove anything"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by bboyhobbit on 2008-05-27
hi guys.

Well, here's the deal.  I installed Kubuntu (Hardy Heron, with KDE 3) on my laptop about a week ago.  liked it a lot, installed KDE 4, liked that a lot too, then decided i wanted to try out Gnome.  so after installing ubuntu-desktop, i decided to remove kde 3,  after googling how to remove it (i'm a newbie) i opened synaptic package manager and removed "kdelibs-data" (which according to a forum, would remove kde (because all kde apps depend on it, i assume.)

Now, whenever i try and "sudo apt-get" anything, i get the following errors (i've used installing nedit as an example here):

vineet@vineet-laptop:~$ sudo apt-get install nedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmotif3
Suggested packages:
  csh
The following packages will be REMOVED
  kio-umountwrapper
The following NEW packages will be installed
  libmotif3 nedit
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2042kB of archives.
After this operation, 4792kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 137374 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)


what's kio-umountwrapper, and why won't remove??

thanks in advance,
bboyhobbit

---

### Post by bboyhobbit on 2008-05-27
i managed to find a fix :D

[https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729](https://bugs.launchpad.net/ubuntu/+source/kio-umountwrapper/+bug/186729)

problem solved!!!

---

