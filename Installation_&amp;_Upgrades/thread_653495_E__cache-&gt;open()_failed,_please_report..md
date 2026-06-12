---
title: "E: _cache-&gt;open() failed, please report."
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by kingrattus on 2007-12-30
I just installed 7.10 on a PII (I just want it as a data server & to learn how to do networking). I tried to add/remove some unwanted programs (games), & this is the error message I got. I don't know how to manually run 'dpkg --configure -a'. I thought if I pasted that in Terminal it would so something.. nope, it says its not a valid command.  So I have no idea what I'm suppose to do.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by taurus on 2007-12-30
Close the Add/Remove window and open a terminal and run these commands.

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kingrattus on 2007-12-30
It failed...


jess@p2:~$ sudo dpkg --configure -a
[sudo] password for jess:
jess@p2:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Reading package lists... Done
jess@p2:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ekiga (2.0.11-1ubuntu1) ...
dpkg: error processing ekiga (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 ekiga
E: Sub-process /usr/bin/dpkg returned an error code (1)
jess@p2:~$

---

### Post by kingrattus on 2007-12-30
For S. & giggles Itried the add/remove again (after those commands).. it worked.

---

### Post by ork on 2008-07-11
Great help guys i had the same problem after powercut and this solved it

---

