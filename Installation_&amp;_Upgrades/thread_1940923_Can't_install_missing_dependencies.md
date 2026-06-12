---
title: "Can't install missing dependencies"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by matt4542 on 2012-03-14
This has been driving me CRAZY for the past two hours.  So I go to install Skype on my new installation of Ubuntu and it fails and the software center keeps asking me to repair the package catalog and when I try to repair it it tells me I am missing dependencies.  Normally I'd just run "sudo apt-get install -f" and it would install the dependencies like normal, but then it outputs an error I haven't seen before.  

> matthew@ubuntu:~$ sudo apt-get install -f
[sudo] password for matthew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 392 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5,143 kB of archives.
After this operation, 3,432 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
matthew@ubuntu:~$ 


Any help would be amazing :)

---

### Post by matt_symes on 2012-03-14
Hi

This is the second time i have seen this error posted in 48 hours. 

Where did you get the .iso for this install ? Can you post a link ?

What have you done since installing ? Please outline everything.

libc-bin and libc are fundamental to any Linux install.

Kind regards

---

