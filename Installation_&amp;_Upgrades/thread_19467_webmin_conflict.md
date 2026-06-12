---
title: "webmin conflict"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by saoday on 2005-03-11
Please help   :grin: 

I just upgraded to Hoary and I can't use synaptic because webmin didn't un-install properly?? 


root@computer1 # apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  webmin-apache: Depends: webmin (>= 1.140) but it is not installable
  webmin-core: Depends: webmin but it is not installable
  webmin-inetd: Depends: webmin (>= 1.140) but it is not installable
  webmin-mysql: Depends: webmin (>= 1.140) but it is not installable
  webmin-proftpd: Depends: webmin (>= 1.140) but it is not installable
  webmin-xinetd: Depends: webmin (>= 1.140) but it is not installable
E: Unmet dependencies. Try using -f.

I tried all possibilities dpkg, install -f, and forumed all day.  It just wont go??  
Please help.

---

### Post by saoday on 2005-03-11
root@computer1# **apt-get -f install**
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  webmin-apache webmin-core webmin-inetd webmin-mysql webmin-proftpd
  webmin-xinetd
0 upgraded, 0 newly installed, 6 to remove and 33 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 14.2MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 87248 files and directories currently installed.)
Removing webmin-apache ...
/var/lib/dpkg/info/webmin-apache.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-apache (--remove):
 subprocess pre-removal script returned error exit status 1
/var/lib/dpkg/info/webmin-apache.postinst: line 4: /usr/sbin/update-webmin: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing webmin-core ...
/var/lib/dpkg/info/webmin-core.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-core (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-inetd ...
/var/lib/dpkg/info/webmin-inetd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-inetd (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-mysql ...
/var/lib/dpkg/info/webmin-mysql.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-mysql (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-proftpd ...
/var/lib/dpkg/info/webmin-proftpd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-proftpd (--remove):
 subprocess pre-removal script returned error exit status 1
Removing webmin-xinetd ...
/var/lib/dpkg/info/webmin-xinetd.prerm: line 5: /usr/sbin/update-webmin: No such file or directory
dpkg: error processing webmin-xinetd (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 webmin-apache
 webmin-core
 webmin-inetd
 webmin-mysql
 webmin-proftpd
 webmin-xinetd
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@computer1: #

---

