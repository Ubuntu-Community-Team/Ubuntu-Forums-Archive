---
title: "dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.6-5ubuntu1_i386."
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by udito on 2010-10-16
Hello,

I have the following issue:

Running
```
root@X100e:/var/cache/apt/archives# apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  file libexpat1 libmagic1 libreadline6 libsqlite3-0 mime-support python python-minimal python2.6 python2.6-minimal readline-common
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5,204kB of archives.
After this operation, 19.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 6108 files and directories currently installed.)
Unpacking python2.6-minimal (from .../python2.6-minimal_2.6.6-5ubuntu1_i386.deb) ...
new installation of python2.6-minimal; /usr/lib/python2.6/site-packages is a directory
which is expected a symlink to /usr/local/lib/python2.6/dist-packages.
please find the package shipping files in /usr/lib/python2.6/site-packages and
file a bug report to ship these in /usr/lib/python2.6/dist-packages instead
aborting installation of python2.6-minimal
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.6-5ubuntu1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.6-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```results in above error.

Running
```
root@X100e:/var/cache/apt/archives# dpkg -i python2.6-minimal_2.6.6-5ubuntu1_i386.deb 
(Reading database ... 6108 files and directories currently installed.)
Unpacking python2.6-minimal (from python2.6-minimal_2.6.6-5ubuntu1_i386.deb) ...
new installation of python2.6-minimal; /usr/lib/python2.6/site-packages is a directory
which is expected a symlink to /usr/local/lib/python2.6/dist-packages.
please find the package shipping files in /usr/lib/python2.6/site-packages and
file a bug report to ship these in /usr/lib/python2.6/dist-packages instead
aborting installation of python2.6-minimal
dpkg: error processing python2.6-minimal_2.6.6-5ubuntu1_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 python2.6-minimal_2.6.6-5ubuntu1_i386.deb

```results in above error.

Running
```
root@X100e:/var/cache/apt/archives# dpkg -i --force-depends python2.6-minimal_2.6.6-5ubuntu1_i386.deb 
(Reading database ... 6108 files and directories currently installed.)
Unpacking python2.6-minimal (from python2.6-minimal_2.6.6-5ubuntu1_i386.deb) ...
new installation of python2.6-minimal; /usr/lib/python2.6/site-packages is a directory
which is expected a symlink to /usr/local/lib/python2.6/dist-packages.
please find the package shipping files in /usr/lib/python2.6/site-packages and
file a bug report to ship these in /usr/lib/python2.6/dist-packages instead
aborting installation of python2.6-minimal
dpkg: error processing python2.6-minimal_2.6.6-5ubuntu1_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 python2.6-minimal_2.6.6-5ubuntu1_i386.deb

```is not able to fix this.

Any clues how to fix this?

---

### Post by viralmeme on 2010-10-16
> **udito said:**
> I have the following issue:

[Sub-Process /usr/bin/dpkg returned an error code (1)]("http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/")

---

### Post by udito on 2010-10-16
issue got solved. see [http://superuser.com/questions/200065/dpkg-error-processing-var-cache-apt-archives-python2-6-minimal-2-6-6-5ubuntu1-i](http://superuser.com/questions/200065/dpkg-error-processing-var-cache-apt-archives-python2-6-minimal-2-6-6-5ubuntu1-i) for details

---

