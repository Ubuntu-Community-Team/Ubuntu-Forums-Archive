---
title: "getting error which we install pure-ftp"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by its_joe on 2007-08-18
Hello,

We get error while installing pure-ftp on the server. 
==============================================
root@server:~# apt-get install pure-ftpd
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  netkit-inetd openbsd-inetd xinetd
The following packages will be REMOVED:
  pure-ftpd-ldap
The following NEW packages will be installed:
  pure-ftpd
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/150kB of archives.
After unpacking 65.5kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 29558 files and directories currently installed.)
Removing pure-ftpd-ldap ...
Stopping ftp server: pure-ftpd.
Selecting previously deselected package pure-ftpd.
(Reading database ... 29546 files and directories currently installed.)
Unpacking pure-ftpd (from .../pure-ftpd_1.0.21-1ubuntu4_i386.deb) ...
Setting up pure-ftpd (1.0.21-1ubuntu4) ...
Starting ftp server: Running: /usr/sbin/pure-ftpd -l pam -O clf:/var/log/pure-ftpd/transfer.log -u 1000 -E -B
invoke-rc.d: initscript pure-ftpd, action "start" failed.
dpkg: error processing pure-ftpd (--configure):
 subprocess post-installation script returned error exit status 252
Errors were encountered while processing:
 pure-ftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
=====================================================

Please suggest us what can be done for this error. ?

thanks
its_joe

---

### Post by cmoad on 2007-10-24
Ditto on this.  I am running into the same problem.  Will let you know if I find a solution.

---

### Post by cmoad on 2007-10-24
Found a fix

[http://forum.openvz.org/index.php?&t=msg&th=791](http://forum.openvz.org/index.php?&t=msg&th=791)

---

