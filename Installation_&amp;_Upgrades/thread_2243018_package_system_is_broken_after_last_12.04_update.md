---
title: "package system is broken after last 12.04 update"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by poum2 on 2014-09-05
Afdter an update on my Ubuntu 12.04, my package system is broken );
The message I get is:
```
The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

>Details
The following packages have unmet dependencies:
libk5crypto3: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.7 is installed
libk5crypto3:i386: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.7 is installed
```

I tried: apt-get -f install
```
poum@poumbuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libevolution screen-resolution-extra libgtkhtml-4.0-common libpst4 bogofilter-bdb libwayland-ltss-server0 calligra-l10n-engb libgtkhtml-4.0-0 evolution-common
  evolution-webcal lib32gcc1 libgtkhtml-editor-4.0-0 bogofilter-common libxrandr-ltss2 bogofilter language-pack-kde-en kde-l10n-engb libvdpau1 libwayland-ltss-client0
  language-pack-kde-en-base nvidia-settings libllvm3.3 libllvm3.3:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libk5crypto3:i386
Suggested packages:
  krb5-doc:i386 krb5-user:i386
The following packages will be upgraded:
  libk5crypto3:i386
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
11 not fully installed or removed.
Need to get 0 B/77.1 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing libk5crypto3:i386 (--configure):
 libk5crypto3:i386 1.10+dfsg~beta1-2ubuntu0.3 cannot be configured because libk5crypto3:amd64 is in a different version (1.10+dfsg~beta1-2ubuntu0.5)
dpkg: error processing libk5crypto3 (--configure):
 libk5crypto3:amd64 1.10+dfsg~beta1-2ubuntu0.5 cannot be configured because libk5crypto3:i386 is in a different version (1.10+dfsg~beta1-2ubuntu0.3)
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libkrb5-3:i386:
 libkrb5-3:i386 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however:
  Package libk5crypto3:i386 is not configured yet.
dpkg: error processing libkrb5-3:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkrb5-3:
 libkrb5-3 depends on libk5crypto3 (>= 1.9+dfsg~beta1); however:
  Package libk5crypto3 is not configured yet.
dpkg: error processing libkrb5-3 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgssapi-krb5-2:
 libgssapi-krb5-2 depends on libk5crypto3 (>= 1.8+dfsg); however:
  Package libk5crypto3 is not configured yet.
 libgssapi-krb5-2 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.5); however:
  Package libkrb5-3 is not configured yet.
dpkg: error processing libgssapi-krb5-2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libgssapi-krb5-2:i386:
 libgssapi-krb5-2:i386 depends on libk5crypto3 (>= 1.8+dfsg); however:
  Package libk5crypto3:i386 is not configured yet.
 libgssapi-krb5-2:i386 depends on libkrb5-3 (= 1.10+dfsg~beta1-2ubuntu0.5); however:
  Package libkrb5-3:i386 is not configured yet.
dpkg: error processing libgssapi-krb5-2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre-headless:
 openjdk-6-jre-headless depends on libkrb5-3 (>= 1.6.dfsg.2); however:
  Package libkrb5-3 is not configured yet.
dpkg: error processing openjdk-6-jre-headless (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao:
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b32-1.13.4-4ubuntu0.12.04.2); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm:
 icedtea-6-jre-jamvm depends on openjdk-6-jre-headless (= 6b32-1.13.4-4ubuntu0.12.04.2); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-jamvm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b32-1.13.4-4ubuntu0.12.04.2); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of openjdk-6-jre-lib:
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b27); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre-lib (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libk5crypto3:i386
 libk5crypto3
 libkrb5-3:i386
 libkrb5-3
 libgssapi-krb5-2
 libgssapi-krb5-2:i386
 openjdk-6-jre-headless
 icedtea-6-jre-cacao
 icedtea-6-jre-jamvm
 openjdk-6-jre
 openjdk-6-jre-lib
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Tried cleaning
```
poum@poumbuntu:~$ sudo apt-get clean
poum@poumbuntu:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
poum@poumbuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libk5crypto3 : Breaks: libk5crypto3:i386 (!= 1.10+dfsg~beta1-2ubuntu0.5) but 1.10+dfsg~beta1-2ubuntu0.3 is installed
 libk5crypto3:i386 : Breaks: libk5crypto3 (!= 1.10+dfsg~beta1-2ubuntu0.3) but 1.10+dfsg~beta1-2ubuntu0.5 is installed
E: Unmet dependencies. Try using -f.
```

I desactivated the whole source list, still the same problem.
Any hint would be greatly apreciated.

---

### Post by TheFu on 2014-09-05
Try using **aptitude**. It is smarter.

If any .deb files have been manually installed, remove them. They are the reason some packages can't be moved forward to newer releases.

---

