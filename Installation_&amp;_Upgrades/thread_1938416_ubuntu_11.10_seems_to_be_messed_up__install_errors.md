---
title: "ubuntu 11.10 seems to be messed up / install errors"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by alex170872 on 2012-03-09
Hi, 

I am using ububtu 11.10 and have sever problems installing something on the system using 

apt-get install

I just tried

> apt-get install python-visual

and got

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglobus-common-doc : Depends: libglobus-common-dev (= 11.6-4) but it is not going to be installed
 libglobus-gsi-callback-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-cert-utils-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-credential-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-openssl-error-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-proxy-core-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-sysconfig-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gssapi-gsi-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-openssl-module-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 python-visual : Depends: libboost-python1.46.1 (>= 1.46.1-1) but it is not going to be installed
                 Depends: libboost-thread1.46.1 (>= 1.46.1-1) but it is not going to be installed
                 Depends: libgtkglextmm-x11-1.2-0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Then I ran 

> sudo apt-get -f install

and I got

<...> 
(Reading database ... 247979 files and directories currently installed.)
Unpacking globus-common-progs (from .../globus-common-progs_11.6-4_i386.deb) ...
Leaving 'diversion of /usr/share/globus/config.guess to /usr/share/globus/config.guess.gpt by globus-common-progs'
dpkg: error processing /var/cache/apt/archives/globus-common-progs_11.6-4_i386.deb (--unpack):
 trying to overwrite '/usr/bin/globus-sh-exec', which is also in package vdt-globus-common 5.0.2r2-2natty
Unpacking libglobus-common-dev (from .../libglobus-common-dev_11.6-4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libglobus-common-dev_11.6-4_i386.deb (--unpack):
 trying to overwrite '/usr/bin/globus-makefile-header', which is also in package vdt-globus-common 5.0.2r2-2natty
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/globus-common-progs_11.6-4_i386.deb
 /var/cache/apt/archives/libglobus-common-dev_11.6-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried to remove one of the globus-common packages which I found with dpkg --get-selections:

> apt-get remove --purge vdt-globus-common

for which I get:

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglobus-common-doc : Depends: libglobus-common-dev (= 11.6-4) but it is not going to be installed
 libglobus-gsi-callback-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-cert-utils-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-credential-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-openssl-error-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-proxy-core-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gsi-sysconfig-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-gssapi-gsi-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 libglobus-openssl-module-dev : Depends: libglobus-common-dev (>= 3) but it is not going to be installed
 vdt-gsi-openssh-client : Depends: vdt-globus-common but it is not going to be installed
 vdt-myproxy-client : Depends: vdt-globus-common but it is not going to be installed
 vdt-myproxy-essentials : Depends: vdt-globus-common but it is not going to be installed
 vdt-uberftp : Depends: vdt-globus-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

goto 10



If anyone know how to get out of this infinite loop, and how to fix my installation system that would be great. If you need other information, please let me know what you need (and where I can find it). 


Thanks
  Alex

---

### Post by jerrrys on 2012-03-09
Just installed it on 12o4 without problem.  Not running 11.10 so don't know for sure whats going on.  Did you update && upgrade before trying to install?

---

### Post by whiskers751 on 2012-03-10
Have you tried sudo dpkg --configure -a?

---

