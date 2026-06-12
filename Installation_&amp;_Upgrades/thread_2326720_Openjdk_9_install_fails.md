---
title: "Openjdk 9 install fails"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by logan33 on 2016-06-03
I'm not sure why, but when I try to install openjdk-9-jdk the install fails...  

Here is the console output:
```
logan@logan:~$ sudo apt-get install openjdk-9-jdkReading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openjdk-9-demo openjdk-9-source visualvm
The following NEW packages will be installed:
  openjdk-9-jdk
0 upgraded, 1 newly installed, 0 to remove and 173 not upgraded.
Need to get 0 B/16.5 kB of archives.
After this operation, 56.3 kB of additional disk space will be used.
(Reading database ... 214508 files and directories currently installed.)
Preparing to unpack .../openjdk-9-jdk_9~b114-0ubuntu1_i386.deb ...
Unpacking openjdk-9-jdk:i386 (9~b114-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/jvm/java-9-openjdk-i386/include/linux/jawt_md.h', which is also in package openjdk-9-jdk-headless:i386 9~b114-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-9-jdk_9~b114-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by ubfan1 on 2016-06-03
Do you need the  openjdk-9-jdk-headless package?  You are getting a complaint about a file (jawt_md.h) being overwritten when you unpack the openjdk-9-jdk.

---

### Post by lapeth2 on 2016-08-19
openjdk-9-jdk depends on openjdk-9-jdk-headless, but at the same time conflicts with it as seen above. My guess is that the dependency should not be there.

---

### Post by ubfan1 on 2016-08-20
Looks like in ...9 that file got added to headless, it's not in the 8 headless, so no conflict.  If you were not starting with no 9 packages, I'd remove them all and reinstall.  I use 8, so I don't see that problem.  This is bug 1550950, you can add yourself to the "does this affect me" but there are already almost 400 in the list.  There are some suggested solutions, like using --force on the install of the second package with the dup.

---

