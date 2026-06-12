---
title: "[SOLVED] Broken Gimp"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by clyde9999 on 2007-10-04
I have tried to fix Gimp using two methods: In synaptic package manager, I attempted to fix the broken package (listed below), to no avail. Then I attempted to fix it using *sudo apt-get -f upgrade*. that also did not work. I am not sure what is next. I also un-installed the package and reinstalled it. Got any ideas anyone? :idea: (I get an error code 1) PS.. I am using Ubuntu 7.10 beta.

clyde9@clyde9-laptop:~$  sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  gimp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/3902kB of archives.
After unpacking 10.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 155620 files and directories currently installed.)
Unpacking gimp (from .../gimp_2.4.0~rc3-1ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb (--unpack):
 trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
clyde9@clyde9-laptop:~$

---

### Post by notwen on 2007-10-04
Check out [this]("http://ubuntuforums.org/showthread.php?p=3474829"). =]

---

### Post by clyde9999 on 2007-10-04
Hi Notwen, 

**Thanks for the fast reply I did it.**

clyde9@clyde9-laptop:~$ sudo dpkg -i --force-all /var/cache/apt/archives/gimp_2.4.0~rc3-1ubuntu5_i386.deb
[sudo] password for clyde9:
(Reading database ... 155620 files and directories currently installed.)
Unpacking gimp (from .../gimp_2.4.0~rc3-1ubuntu5_i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/doc/libgimp2.0/README', which is also in package libgimp2.0
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/share/doc/libgimp2.0/README.Debian', which is also in package libgimp2.0
Setting up gimp (2.4.0~rc3-1ubuntu5) ...

**This was the ticket!! Thanks Notwen, have a cup of java on me friend!**):P

---

### Post by notwen on 2007-10-04
Glad it worked for you, be sure to mark this thread as solved using the thread-tools option. =]

---

