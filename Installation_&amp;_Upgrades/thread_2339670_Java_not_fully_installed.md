---
title: "Java not fully installed ???"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by matthew743 on 2016-10-11
Tried to install the latest java jdk and it returned an error on the install.  did " sudo apt-get -f install "  with negative results.  Tried to uninstall it and got the same error and required "sudo apt-get -f install"  with same error message listed below

```
Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Correcting dependencies... Done
 The following package was automatically installed and is no longer required:
   linux-image-extra-4.4.0-31-generic
 Use 'sudo apt autoremove' to remove it.
 The following additional packages will be installed:
   openjdk-9-jdk
 Suggested packages:
   visualvm
 The following NEW packages will be installed:
   openjdk-9-jdk
 0 upgraded, 1 newly installed, 0 to remove and 119 not upgraded.
 45 not fully installed or removed.
 Need to get 0 B/16.6 kB of archives.
 After this operation, 58.4 kB of additional disk space will be used.
 Do you want to continue? [Y/n] y
 (Reading database ... 284524 files and directories currently installed.)
 Preparing to unpack .../openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb ...
 Unpacking openjdk-9-jdk:amd64 (9~b114-0ubuntu1) ...
 dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb (--unpack):
  trying to overwrite '/usr/lib/jvm/java-9-openjdk-amd64/include/linux/jawt_md.h', which is also in package openjdk-9-jdk-headless:amd64 9~b114-0ubuntu1
 Errors were encountered while processing:
  /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb
 E: Sub-process /usr/bin/dpkg returned an error code (1)
```


The whole idea is to get brasero or some DVD burning software to work and they all require java so I can not now burn cds or dvds.

any help is greatly appreciated

---

