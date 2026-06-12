---
title: "/usr/bin/dpkg returned an error code (1)"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by anspliff on 2010-03-19
Hi I'm tried to install bandwidthd on Ubuntu 9.10 and keep getting the following error.
Sorry if this is a repeat post I have been looking around for a while and have been unsuccessful in finding a answer.


[HTML] $sudo apt-get install bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevent-1.4-2
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
18 not fully installed or removed.
Need to get 0B/71.8kB of archives.
After this operation, 57.3kB of additional disk space will be used.
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
(Reading database ... 164391 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20071208-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20071208-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]

---

### Post by anspliff on 2010-03-20
::SOLVED::

        I'm sorry I looked threw some post and was able to fix it.... Thank you any ways.

---

