---
title: "update Problem"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by garymc1 on 2007-05-08
when i use the following command sudo apt-get upgrade i get the following error 

garymc@garymc-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
libcurl3 libcurl3-gnutls python-pam synaptic
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1396kB of archives.
After unpacking 65.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb (--unpack):
failed in buffer_read(fd): files list for package `hicolor-icon-theme': Input/output error
Errors were encountered while processing:
/var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by taurus on 2007-05-08
Try

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by garymc1 on 2007-05-08
when i got to the last command (sudo aptitude upgrade) i got the following error 

(Reading database ... 
dpkg: serious warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `hicolor-icon-theme': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
garymc@garymc-desktop:~$

---

### Post by pkg on 2007-05-08
I get following errors when running "update manager"


E: Type 'wget' is not known on line 49 in source list /etc/apt/sources.list
E: Couldn't read list of package sources

thanks

---

### Post by garymc1 on 2007-05-11
Any one got any ideas how I can solve this error 

garymc@garymc-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
libcurl3 libcurl3-gnutls python-pam synaptic
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1396kB of archives.
After unpacking 65.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ...
dpkg: serious warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb (--unpack):
failed in buffer_read(fd): files list for package `hicolor-icon-theme': Input/output error
Errors were encountered while processing:
/var/cache/apt/archives/libcurl3_7.15.4-1ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by garymc1 on 2007-05-13
Any one know of a solution are will have to re-install ??? if I reinstall will i have to back up all my data are will it still remain in the home directory

---

### Post by Nossie on 2007-06-04
hey :)

have you tried just going to 

/etc/apt

renaming sources.list to sources.list.bak and rerunning those commands?

seems to have worked for me....

---

