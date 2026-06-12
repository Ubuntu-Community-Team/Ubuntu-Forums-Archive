---
title: "apt-get has the wrong idea"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by hosk on 2007-07-29
i generally can't install any packages because there exists some bottom level dependency that doesn't exist at all; thus the packages refuse to install.  i give you an example:

```

hosk@hosk-desktop:~$ sudo apt-get install docbook-xml
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
core (>= 0.5) but it is not installable
E: Broken packages

```

As you can see, it should depend on xml-core, which I already have installed.  It's generally like that for most packages, since everything depends on scrollkeeper and scrollkeeper depends on docbook-xml.

Any assistance?
Thanks!

---

### Post by hosk on 2007-07-29
Another option I'm open to but I'm not sure exists, is there a way to reinstall my 7.04 install from the CD but keep all the extra packages and upgraded ones?

---

### Post by hosk on 2007-07-29
and while i'm at it, here's another anomaly
```

hosk@hosk-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dmsetup
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hosk@hosk-desktop:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Starting
Starting 2
Investigating dmsetup
Package dmsetup has broken dep on libc6
 Try to Re-Instate dmsetup
Done
Done
The following packages have been kept back:
  dmsetup
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hosk@hosk-desktop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

I would *love* help on fixing any of these problems...

---

### Post by rillip on 2007-07-29
Have you tried 

```
 sudo apt-get install -f
```

This should force it to fix broken packages

---

### Post by hosk on 2007-07-29
actually, sudo apt-get install -f is the problem, the first time i tried it, it started uninstalling a huge number of packages because it wanted to install something called libjaRper instead of libjasper

```

hosk@hosk-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java libcommons-pool-java liblucene-java eclipse-rcp
  libcommons-el-java junit libregexp-java libcommons-modeler-java
  anjuta-common libservlet2.4-java libtomcat5.5-java libbcel-java ant
  libcommons-launcher-java libcommons-logging-java libcommons-dbcp-java
  libcommons-collections-java libcommons-beanutils-java
  libcommons-digester-java liblucene-java-doc libjsch-java ant-optional
  libmx4j-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by hosk on 2007-07-29
here we go, i made it want to install libjaRper again
```

hosk@hosk-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java libcommons-pool-java liblucene-java eclipse-rcp
  libcommons-el-java junit libregexp-java libcommons-modeler-java
  anjuta-common libservlet2.4-java libtomcat5.5-java libbcel-java ant
  libcommons-launcher-java libcommons-logging-java libcommons-dbcp-java
  libcommons-collections-java libcommons-beanutils-java
  libcommons-digester-java liblucene-java-doc libjsch-java ant-optional
  libmx4j-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjaRper-1.701-1
The following NEW packages will be installed:
  libjaRper-1.701-1
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/135kB of archives.
After unpacking 348kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 125660 files and directories currently installed.)
Preparing to replace libjasper-1.701-1 1.701.0-2 (using .../libjaRper-1.701-1_1.701.0-2_i386.deb) ...
Unpacking replacement libjasper-1.701-1 ...
dpkg: error processing libjarper-1.701-1 (--configure):
 no package named `libjarper-1.701-1' is installed, cannot configure
dpkg: dependency problems prevent configuration of libjasper-runtime:
 libjasper-runtime depends on libjasper-1.701-1 (>= 1.701.0); however:
  Package libjasper-1.701-1 is not configured yet.
dpkg: error processing libjasper-runtime (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libjarper-1.701-1
 libjasper-runtime
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't help but think something on my filesystem is corrupted, but fsck on my ext3 partition doesn't return anything.

---

### Post by hosk on 2007-07-30
yep, totally going to obsessively bump this in hopes of getting a reply.

---

### Post by Ryoushi19 on 2007-07-30
I had this same problem at some point, it's usally because of a package which is "too new" for your version.  For example, a 7.10 package on 7.04.  It's not that you don't have the package, it's that it's not new enough.  Update your sources.list to fix it up.

---

