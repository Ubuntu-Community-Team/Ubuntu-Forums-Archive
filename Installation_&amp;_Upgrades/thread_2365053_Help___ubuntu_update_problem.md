---
title: "Help   ubuntu update problem"
date: 2017-07-01
forum: Installation &amp; Upgrades
---

### Post by firsttimeuser3 on 2017-07-01
when i always run update i get this message      :


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 1,081 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://mirror.nl.leaseweb.net/ubuntu](http://mirror.nl.leaseweb.net/ubuntu) xenial-updates/main amd64 libssl1.0.0 amd64 1.0.2g-1ubuntu4.8 [1,081 kB]
Fetched 1,081 kB in 3s (314 kB/s)        
dpkg: error processing package libssl1.0.0:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of libdns162:amd64:
 libdns162:amd64 depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:amd64 is not configured yet.

dpkg: error processing package libdns162:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of libisccfg140:amd64:
 libisccfg140:amd64 depends on libdns162; however:
  Package libdns162:amd64 is not configured yet.

dpkg: error processing package libisccfg140:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbind9-140:amd64:
 libbind9-140:amd64 depends on libdns162; however:
  Package libdns162:amd64 is not configured yet.
 libbind9-140:amd64 depends on libisccfg140; however:
  Package libisccfg140:amd64 is not configured yet.

dpkg: error processing package libbind9-140:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libbind9-140 (= 1:9.10.3.dfsg.P4-8ubuntu1.7); however:
  Package libbind9-140:amd64 is not configured yet.
 bind9-host depends on libdns162 (= 1:9.10.3.dfsg.P4-8ubuntu1.7); however:
  Package libdns162:amd64 is not configured yet.
 bind9-host depends No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
          on libisccfg140 (= 1:9.10.3.dfsg.P4-8ubuntu1.7); however:
  Package libisccfg140:amd64 is not configured yet.

dpkg: error processing package bind9-host (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libbind9-140 (= 1:9.10.3.dfsg.P4-8ubuntu1.7); however:
  Package libbind9-140:amd64 is not configured yet.
 dnsutils depends on libdns162 (= 1:9.10.3.dfsg.P4-8ubuntu1.7); however:
  Package libdns162:amd64 is not configured yet.
 dnsutils depends on libisccfg140 (= 1:9.10.3.dfsg.P4-8ubuntu1.7); however:
  Package libisccfg140:amd64 is not configured yet.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.

dpkg: error processing package dnsutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssl:
 opNo apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               enssl depends on libssl1.0.0 (>= 1.0.2g); however:
  Package libssl1.0.0:amd64 is not configured yet.

dpkg: error processing package openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-4.4.0-83-generic:
 linux-headers-4.4.0-83-generic depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:amd64 is not configured yet.

dpkg: error processing package linux-headers-4.4.0-83-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-4.4.0-83-generic; however:
  Package linux-headers-4.4.0-83-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 4.4.0.83.89); however:
  PackNo apport report written because MaxReports is reached already
                                                                    age linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-4.8.0-58-generic:
 linux-headers-4.8.0-58-generic depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:amd64 is not configured yet.

dpkg: error processing package linux-headers-4.8.0-58-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-hwe-16.04:
 linux-headers-generic-hwe-16.04 depends on linux-headers-4.8.0-58-generic; however:
  Package linux-headers-4.8.0-58-generic is not configured yet.

dpkg: error processing package linux-headers-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-headers-generic-hwe-16.04 (= 4.8.0.58.29); however:
  Package linux-headers-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-4.8.0-56-generic:
 linux-headers-4.8.0-56-generic depends on libssl1.0.0 (>= 1.0.0); however:
  Package libssl1.0.0:amd64 is not configured yet.

dpkg: error processing package linux-headers-4.8.0-56-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libssl1.0.0:amd64
 libdns162:amd64
 libisccfg140:amd64
 libbind9-140:amd64
 bind9-host
 dnsutils
 openssl
 linux-headers-4.4.0-83-generic
 linux-headers-generic
 linux-generic
 linux-headers-4.8.0-58-generic
 linux-headers-generic-hwe-16.04
 linux-generic-hwe-16.04
 linux-headers-4.8.0-56-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ani@ani-HP-ProBook-4530s:~$ 
someone help me plz


```

---

### Post by Bashing-om on 2017-07-01
firsttimeuser3; Hello; Welcome to the forum.

As we have :
> 
XXXXX is not configured yet.

Let's try and see if the package manager will "fix" for us.
try:
```

sudo dpkg --configure -a
sudo apt update
sudo apt full-upgrade
sudo apt -f install

```
Post back - between code tags - if there are any reported errors that the package manager will not fix .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we see what steps need to be taken.

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

