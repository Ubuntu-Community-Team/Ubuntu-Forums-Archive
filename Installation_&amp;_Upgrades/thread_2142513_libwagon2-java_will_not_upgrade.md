---
title: "libwagon2-java will not upgrade"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by 65 mustang on 2013-05-05
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libwagon2-java
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,052 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/universe libwagon2-java all 2.2-3+nmu1 [1,052 kB]
Fetched 1,052 kB in 12s (84.7 kB/s)                                                                                                                                                                                                                                                      
(Reading database ... 393394 files and directories currently installed.)
Preparing to replace libwagon2-java 2.2-3 (using .../libwagon2-java_2.2-3+nmu1_all.deb) ...
Unpacking replacement libwagon2-java ...
dpkg: error processing /var/cache/apt/archives/libwagon2-java_2.2-3+nmu1_all.deb (--unpack):
 trying to overwrite '/usr/share/java/wagon-tck-http.jar', which is also in package libwagon-java 1.0.0-2ubuntu2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libwagon2-java_2.2-3+nmu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

