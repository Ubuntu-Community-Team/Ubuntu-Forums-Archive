---
title: "procps dependency hell when dist-upgrade to precise"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by masuch on 2012-04-26
Hi,

I have been trying to solve problem with installation of procps but I did not succeed. Could please anybody help me to investigate how to fix it ?

---ERROR:
Setting up procps (1:3.2.8-11ubuntu6) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1

(
--- sudo dpkg --configure -a ... same error
--- sudo apt-get install --reinstall procps ... same error.
--- sudo apt-get remove/purge procps ... gave me this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 apache2.2-common : Depends: procps
 erlang-crypto : Depends: erlang-base (= 1:14.b.4-dfsg-1ubuntu1) but it is not going to be installed or
                          erlang-base-hipe (= 1:14.b.4-dfsg-1ubuntu1) but it is not going to be installed
 ia32-libs : Depends: ia32-libs-multiarch
 libmikmod2 : Depends: oss-compat but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


Thank You,
Kind Regards,
M.

---

### Post by jadtech on 2012-04-26
check this out 

[http://ubuntuforums.org/showthread.php?t=1505356](http://ubuntuforums.org/showthread.php?t=1505356)

---

### Post by masuch on 2012-04-26
... thank you , thank you , thank you. 

problem was easy to solve:
I had
net.ipv4.ip_local_port_range = 16384 65536
instead of 
net.ipv4.ip_local_port_range = 16384 65535



thank you.
M.

P.S. 
I had to have this problem earlier but I did not noticed it util now. My bad.

---

### Post by icemanxp on 2012-05-17
Hey just to let you know I had a similar issue doing an upgrade to 12.04, I traced it down to a previous version of iscsitarget causing procps not to start.
The solution is to move 30-iscsitarget.conf out of /etc/sysctl.d/ and letting the package manager install the new version.

---

