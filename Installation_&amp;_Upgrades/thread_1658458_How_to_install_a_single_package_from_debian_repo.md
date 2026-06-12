---
title: "How to install a single package from debian repo??"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by mark_101 on 2011-01-02
Hi,

I wish to use encfs, however there were several security vulns ([http://seclists.org/fulldisclosure/2010/Aug/316](http://seclists.org/fulldisclosure/2010/Aug/316)) that now seem to have been fixed ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595998](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595998)) in version 1.7.2-1.

It looks like this version will be merged into Natty, however I wish to use it now on 10.04.  How do I go about getting 1.7.2-1 of encfs from the debian main?  I'm guessing if I add their repo to my unbuntu 10.04 install then it would cause all kinds of grief with other incorrect dependencies!


Many thanks in advance for any guidance on this

Mark

---

### Post by lithopsian on 2011-01-02
If you can find a deb built for Lucid, that would be better, but if not then give it a try.  First off it might refuse because of dependencies it knows about.  You could override that but often it will fail since the dependencies are there for a reason.   If it installs and doesn't work uninstall it.  Something like this is unlikely to send you to a state where you can't boot.

---

### Post by mark_101 on 2011-01-03
Hi,

thanks for the info.  I managed to find an rpm from debian, converted this with "alien -k" and now have some dependency issues.  This is something I've not had to deal with before -  how do I resolve this type of problem? 


[LIST]
[*]I first completely removed encfs using synaptic
[*]Then I installed the latest encfs deb file
[*]Lastly I tried to install pam using the following -
[/LIST]
[INDENT]```
sudo apt-get install libpam-encfs
```[/INDENT]Which unfortunately gives me this - 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  encfs
The following NEW packages will be installed
  encfs libpam-encfs
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 382kB of archives.
After this operation, 1,819kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe encfs 1.5.2-2 [370kB]
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe libpam-encfs 0.1.4.1-4 [12.2kB]
Fetched 382kB in 0s (1,398kB/s)      
Selecting previously deselected package encfs.
(Reading database ... 297209 files and directories currently installed.)
Unpacking encfs (from .../encfs_1.5.2-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/encfs_1.5.2-2_i386.deb (--unpack):
 trying to overwrite '/usr/bin/encfs', which is also in package fuse-encfs 0:1.7.2-1.fc13
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package libpam-encfs.
Unpacking libpam-encfs (from .../libpam-encfs_0.1.4.1-4_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/encfs_1.5.2-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Any ideas??

Thanks

Mark

---

### Post by foppeh on 2011-02-03
From the output above the error is
```
trying to overwrite '/usr/bin/encfs', which is also in package fuse-encfs 0:1.7.2-1.fc13
```
which means you want to uninstall fuse-encfs. Please don't use Synaptic for non-standard operations. Use commandline `dpkg` instead.

Also have a look at [UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports") and/or [Apt-Pinning for Beginners]("http://jaqque.sbih.org/kplug/apt-pinning.html") which may or may not solve your issue by adding the future Ubuntu repository or Debian Unstable alongside current Ubuntu. I strongly advise to test such a setup in a clean VirutalMachine before you ruin your desktop.

---

