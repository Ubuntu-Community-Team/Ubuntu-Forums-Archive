---
title: "OpenJDK-6-JRE"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by NSim on 2010-04-27
Hi,
I am trying to install OpenJdk-6-Jre on my system, but I get the folowing error:
--------------------------------------------------------------------------
host% sudo apt-get install openjdk-6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaccess-bridge-java libaccess-bridge-java-jni
Suggested packages:
  icedtea6-plugin
The following NEW packages will be installed:
  libaccess-bridge-java libaccess-bridge-java-jni openjdk-6-jre
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 3,676B/672kB of archives.
After this operation, 1,421kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libaccess-bridge-java-jni openjdk-6-jre libaccess-bridge-java
Install these packages without verification [y/N]? y
Get:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) lucid/main libaccess-bridge-java-jni 1.26.2-3 [3,676B]
Fetched 3,676B in 0s (270kB/s)                      
Selecting previously deselected package libaccess-bridge-java-jni.
(Reading database ... 154400 files and directories currently installed.)
Unpacking libaccess-bridge-java-jni (from .../libaccess-bridge-java-jni_1.26.2-3_i386.deb) ...
Selecting previously deselected package openjdk-6-jre.
Unpacking openjdk-6-jre (from .../openjdk-6-jre_6b18-1.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package libaccess-bridge-java.
Unpacking libaccess-bridge-java (from .../libaccess-bridge-java_1.26.2-3_all.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up openjdk-6-jre-headless (6b18-1.8-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing openjdk-6-jre-headless (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b18-1.8-0ubuntu1); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up libaccess-bridge-java (1.26.2-3) ...
Setting up libaccess-bridge-java-jni (1.26.2-3) ...

dpkg: dependency problems prevent configuration of ca-certificates-java:
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however:
  Package openjdk-6-jre-headless is not configured yet.
  Package java6-runtime-headless is not installed.
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet.
dpkg: error processing ca-certificates-java (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 openjdk-6-jre-headless
 openjdk-6-jre
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)
--------------------------------------------------------------------------------------------------
Even if I try to remove it a get this following  massage
"E: openjdk-6-jre-headless: subprocess installed pre-removal script returned error exit status 2"
And of course a broken package  openjdk-6-jre-headless?
Any suggestions how to solve this problem?

---

### Post by donsy on 2010-04-27
Did you try to repair the broken package in Synaptic?

```
System > Administration > Synaptic Package Manager

Click on the button "Custom Filters".

Then look for "Broken" which should appear just under "All".

```

---

### Post by NSim on 2010-04-28
Yes I know were I can find it, but unfortunately I can't remove it. I think something is wrong with dpkg, i don't know....

---

### Post by NSim on 2010-04-29
[http://ubuntuforums.org/showthread.php?t=1461045](http://ubuntuforums.org/showthread.php?t=1461045) 

This solved my problem......

---

