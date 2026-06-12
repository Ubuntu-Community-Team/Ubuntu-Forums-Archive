---
title: "Java not fully installed ???"
date: 2016-10-11
forum: Installation &amp; Upgrades
---

### Post by matthew743 on 2016-10-11
Tried to install the latest java jdk and it returned an error on the install.  did " sudo apt-get -f install "  with negative results.  Tried to uninstall it and got the same error and required "sudo apt-get -f install"  with same error message listed below

   [SIZE=3]Reading package lists... Done[/SIZE]
 [SIZE=3]Building dependency tree       [/SIZE] 
 [SIZE=3]Reading state information... Done[/SIZE]
 [SIZE=3]Correcting dependencies... Done[/SIZE]
 [SIZE=3]The following package was automatically installed and is no longer required:[/SIZE]
   [SIZE=3]linux-image-extra-4.4.0-31-generic[/SIZE]
 [SIZE=3]Use 'sudo apt autoremove' to remove it.[/SIZE]
 [SIZE=3]The following additional packages will be installed:[/SIZE]
   [SIZE=3]openjdk-9-jdk[/SIZE]
 [SIZE=3]Suggested packages:[/SIZE]
   [SIZE=3]visualvm[/SIZE]
 [SIZE=3]The following NEW packages will be installed:[/SIZE]
   [SIZE=3]openjdk-9-jdk[/SIZE]
 [SIZE=3]0 upgraded, 1 newly installed, 0 to remove and 119 not upgraded.[/SIZE]
 [SIZE=3]45 not fully installed or removed.[/SIZE]
 [SIZE=3]Need to get 0 B/16.6 kB of archives.[/SIZE]
 [SIZE=3]After this operation, 58.4 kB of additional disk space will be used.[/SIZE]
 [SIZE=3]Do you want to continue? [Y/n] y[/SIZE]
 [SIZE=3](Reading database ... 284524 files and directories currently installed.)[/SIZE]
 [SIZE=3]Preparing to unpack .../openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb ...[/SIZE]
 [SIZE=3]Unpacking openjdk-9-jdk:amd64 (9~b114-0ubuntu1) ...[/SIZE]
 [SIZE=3]dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb (--unpack):[/SIZE]
  [SIZE=3]trying to overwrite '/usr/lib/jvm/java-9-openjdk-amd64/include/linux/jawt_md.h', which is also in package openjdk-9-jdk-headless:amd64 9~b114-0ubuntu1[/SIZE]
 [SIZE=3]Errors were encountered while processing:[/SIZE]
  [SIZE=3]/var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_amd64.deb[/SIZE]
 [SIZE=3]E: Sub-process /usr/bin/dpkg returned an error code (1)[/SIZE]


The whole idea is to get brasero or some DVD burning software to work and they all require java so I can not now burn cds or dvds.

any help is greatly appreciated

---

### Post by QIII on 2016-10-11
Duplicate of [https://ubuntuforums.org/showthread.php?t=2339670](https://ubuntuforums.org/showthread.php?t=2339670)

Closed.

---

