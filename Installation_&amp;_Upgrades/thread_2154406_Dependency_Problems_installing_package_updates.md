---
title: "Dependency Problems installing package updates"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by BrettD123 on 2013-06-14
Hi,
I'm having problems updating my packages because of dependencies.  Please help!  My output is:

> 
brett@EZserver:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-server : Depends: linux-image-3.2.0-45-generic but it is not installed
 linux-server : Depends: linux-headers-server (= 3.2.0.45.54) but 3.2.0.48.58 is installed
E: Unmet dependencies. Try using -f.

brett@EZserver:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-39-generic linux-image-3.2.0-37-generic linux-headers-3.2.0-41 linux-headers-3.2.0-43 linux-headers-3.2.0-39
  linux-image-3.2.0-40-generic linux-image-3.2.0-43-generic linux-image-3.2.0-38-generic linux-headers-3.2.0-43-generic linux-image-3.2.0-41-generic
  linux-image-3.2.0-39-generic linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-server linux-server
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,096 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-45-generic; however:
  Package linux-image-3.2.0-45-generic is not installed.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.45.54); however:
  Package linux-image-server is not configured yet.
 linux-server depends on linux-headers-server (= 3.2.0.45.54); however:
  Version of linux-headers-server on system is 3.2.0.48.58.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                          Errors were encountered while processing:
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2013-06-14
BrettD123; Hi ! Welcome to the forum .

This is sort of messing with my head:
> Package linux-image-server is not configured yet.
linux-server depends on linux-headers-server (= 3.2.0.45.54); however:
Version of linux-headers-server on system is 3.2.0.48.58.

Lets see the results of terminal code:
```
sudo apt-get dist-upgrade
``` in the event the situation is not corrected, will give some more info to work from.

[INDENT]a good mystery here beats a good mystery on the couch[/INDENT]

---

### Post by BrettD123 on 2013-06-14
> **Bashing-om said:**
> BrettD123; Hi ! Welcome to the forum .

This is sort of messing with my head:


Lets see the results of terminal code:
```
sudo apt-get dist-upgrade
``` in the event the situation is not corrected, will give some more info to work from.
[INDENT]a good mystery here beats a good mystery on the couch[/INDENT]


Thanks.
The following is the output:

> brett@EZserver:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-server : Depends: linux-image-3.2.0-45-generic but it is not installed
 linux-server : Depends: linux-headers-server (= 3.2.0.45.54) but 3.2.0.48.58 is installed
E: Unmet dependencies. Try using -f.

brett@EZserver:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-39-generic linux-image-3.2.0-37-generic linux-headers-3.2.0-41 linux-headers-3.2.0-43
  linux-headers-3.2.0-39 linux-image-3.2.0-40-generic linux-image-3.2.0-43-generic linux-image-3.2.0-38-generic
  linux-headers-3.2.0-43-generic linux-image-3.2.0-41-generic linux-image-3.2.0-39-generic linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-server linux-server
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,096 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-45-generic; however:
  Package linux-image-3.2.0-45-generic is not installed.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.45.54); however:
  Package linux-image-server is not configured yet.
 linux-server depends on linux-headers-server (= 3.2.0.45.54); however:
  Version of linux-headers-server on system is 3.2.0.48.58.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                   Errors were encountered while processing:
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]BrettD123; Welp...

Doesn't help us a whole bunch ... time to roll our sleeves up and go to work. Let's look and see what we are working from:
```
uname -a
ls -la /boot/
```
and then -see about how to "simplify the equation"
[/COLOR][INDENT=2][COLOR=#000000]
one small step

 [/COLOR][/INDENT]

---

### Post by fantab on 2013-06-14
You can try:

```
sudo dpkg --purge linux-image-server linux-server
sudo apt-get remove --purge linux-image-server linux-server
sudo apt-get autoremove
sudo apt-get clean 
sudo apt-get -f install
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by dmw801 on 2013-06-21
I had this same error.. I think it was caused because I only have 100MB on my /boot partition, the auto-upgrade failed, and I had to manually delete a bunch of stuff from /boot.  Then, apt-get failed, and I'm thinking the ubuntu package maintainers (maybe?) got rid of the .45 package and replaced it with .48, so the dependencies got confused.. anyway, these commands seemed to fix things, at least to where I could use apt-get again (but I haven't yet tried rebooting):

sudo dpkg -i /var/cache/apt/archives/linux-image-generic_3.2.0.48.58_amd64.deb
sudo dpkg -i /var/cache/apt/archives/linux-generic_3.2.0.48.58_amd64.deb

Also, the 3.2.0.48.58 packages were current as of this writing (2013-06-20), but will likely be different in the near future.  Good luck!

---

### Post by ronjamarieann on 2013-06-26
Thank you dmw801, I had the same error but after freeing space on /boot the suggested commands like 

sudo dpkg --configure -a
sudo apt-get install -f

did not help. This anyhow seems to fix the missmatched dependencies.

---

### Post by Blazer79 on 2013-09-28
Thank you! This solved my problem!!

Had the same problem but different image version (.53 stuck asking for .43 as dependency) 

> **fantab said:**
> You can try:

```
sudo dpkg --purge linux-image-server linux-server
sudo apt-get remove --purge linux-image-server linux-server
sudo apt-get autoremove
sudo apt-get clean 
sudo apt-get -f install
sudo apt-get update && sudo apt-get dist-upgrade
```

---

