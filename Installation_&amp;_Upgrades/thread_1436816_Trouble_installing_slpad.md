---
title: "Trouble installing slpad"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by LonelyStar on 2010-03-23
Hi,

I was trying to install slapd (I think I once had it installed, by removed it).

I get:
```

sudo apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns43
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1467kB of archives.
After this operation, 3965kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package slapd.
(Reading database ... 77449 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.11-0ubuntu6.2_i386.deb) ...
Processing triggers for man-db ...
Setting up slapd (2.4.11-0ubuntu6.2) ...
  Backing up /etc/ldap/slapd.d/ in /var/backups/slapd-2.4.11-0ubuntu6... done.
chown: cannot access `olcDbDirectory\nolcDbDirectory': No such file or directory
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
So what is the problem her?
What is olcDbDirectory\nolcDbDirectory' why does it not exists?

Ideas?
Thanks!
Nathan

---

