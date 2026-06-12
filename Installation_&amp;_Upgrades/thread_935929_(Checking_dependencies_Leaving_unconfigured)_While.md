---
title: "(Checking dependencies: Leaving unconfigured) While updating"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by vivek1985 on 2008-10-02
I am getting the following error while installing or updating  any software

Plz help me..
E: gij-4.2: subprocess post-installation script returned error exit status 2
E: ecj: dependency problems - leaving unconfigured
E: libecj-java-gcj: subprocess post-installation script returned error exit status 2
E: ecj-gcj: dependency problems - leaving unconfigured
E: gappletviewer-4.2: dependency problems - leaving unconfigured
E: gcj-4.2: dependency problems - leaving unconfigured
E: libgcj8-dev: dependency problems - leaving unconfigured
E: gij: dependency problems - leaving unconfigured
E: java-gcj-compat-headless: dependency problems - leaving unconfigured
E: java-gcj-compat: dependency problems - leaving unconfigured
E: liblog4j1.2-java: dependency problems - leaving unconfigured
E: antlr: dependency problems - leaving unconfigured
E: gjdoc: dependency problems - leaving unconfigured
E: java-gcj-compat-dev: dependency problems - leaving unconfigured
E: libjaxp1.3-java: dependency problems - leaving unconfigured
E: libxerces2-java: dependency problems - leaving unconfigured
E: ant: dependency problems - leaving unconfigured
E: libjsch-java: dependency problems - leaving unconfigured
E: liblucene-java: dependency problems - leaving unconfigured
E: libcommons-collections3-java: dependency problems - leaving unconfigured
E: libcommons-pool-java: dependency problems - leaving unconfigured
E: libcommons-collections-java: dependency problems - leaving unconfigured
E: libcommons-dbcp-java: dependency problems - leaving unconfigured
E: libservlet2.4-java: dependency problems - leaving unconfigured
E: libcommons-el-java: dependency problems - leaving unconfigured
E: libservlet2.3-java: dependency problems - leaving unconfigured
E: libcommons-logging-java: dependency problems - leaving unconfigured
E: libcommons-launcher-java: dependency problems - leaving unconfigured
E: libcommons-beanutils-java: dependency problems - leaving unconfigured
E: libcommons-digester-java: dependency problems - leaving unconfigured
E: libcommons-modeler-java: dependency problems - leaving unconfigured
E: libtomcat5.5-java: dependency problems - leaving unconfigured
E: eclipse-platform: dependency problems - leaving unconfigured
E: eclipse-cdt: dependency problems - leaving unconfigured
E: libregexp-java: dependency problems - leaving unconfigured
E: libbcel-java: dependency problems - leaving unconfigured
E: libmx4j-java: dependency problems - leaving unconfigured

---

### Post by Partyboi2 on 2008-10-02
If you open a terminal (Applications>Accessories>Terminal) and typed[FONT=monospace]
[/FONT]```
sudo dpkg --configure -a
``` What is the output?

---

### Post by oldos2er on 2008-10-02
Could you please copy and paste the output of "cat /etc/apt/sources.list"?

---

### Post by vivek1985 on 2008-10-02
vivek@vivek-desktop:~$ sudo dpkg --configure -a
[sudo] password for vivek: 
Setting up gij-4.2 (4.2.4-1ubuntu2) ...
gcj-dbtool-4.2: error while loading shared libraries: libgcj.so.81: cannot open shared object file: No such file or directory
dpkg: error processing gij-4.2 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libecj-java-gcj (3.3.0+0728-5) ...
gcj-dbtool-4.2: error while loading shared libraries: libgcj.so.81: cannot open shared object file: No such file or directory
dpkg: error processing libecj-java-gcj (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of java-gcj-compat-headless:
 java-gcj-compat-headless depends on gij-4.2 (>= 4.2.1-3); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing java-gcj-compat-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcj-4.2:
 gcj-4.2 depends on gij-4.2 (= 4.2.4-1ubuntu2); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gcj-4.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gappletviewer-4.2:
 gappletviewer-4.2 depends on gij-4.2 (= 4.2.4-1ubuntu2); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gappletviewer-4.2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat:
 java-gcj-compat depends on java-gcj-compat-headless (= 1.0.77-2ubuntu2); however:
  Package java-gcj-compat-headless is not configured yet.
dpkg: error processing java-gcj-compat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ecj:
 ecj depends on gij-4.2 (>= 4.2.1); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing ecj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-el-java:
 libcommons-el-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-el-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-dbcp-java:
 libcommons-dbcp-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-dbcp-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ecj-gcj:
 ecj-gcj depends on ecj (>= 3.3.0+0728-5); however:
  Package ecj is not configured yet.
 ecj-gcj depends on libecj-java-gcj (>= 3.3.0+0728-5); however:
  Package libecj-java-gcj is not configured yet.
dpkg: error processing ecj-gcj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gij:
 gij depends on gij-4.2 (>= 4.2.3-1); however:
  Package gij-4.2 is not configured yet.
dpkg: error processing gij (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-modeler-java:
 libcommons-modeler-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-modeler-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-logging-java:
 libcommons-logging-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-logging-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of java-gcj-compat-dev:
 java-gcj-compat-dev depends on ecj-gcj (>= 3.3.0+0728); however:
  Package ecj-gcj is not configured yet.
 java-gcj-compat-dev depends on gappletviewer-4.2; however:
  Package gappletviewer-4.2 is not configured yet.
 java-gcj-compat-dev depends on gcj-4.2; however:
  Package gcj-4.2 is not configured yet.
 java-gcj-compat-dev depends on java-gcj-compat (= 1.0.77-2ubuntu2); however:
  Package java-gcj-compat is not configured yet.
dpkg: error processing java-gcj-compat-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of antlr:
 antlr depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing antlr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-beanutils-java:
 libcommons-beanutils-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 libcommons-beanutils-java depends on libcommons-logging-java; however:
  Package libcommons-logging-java is not configured yet.
dpkg: error processing libcommons-beanutils-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-collections-java:
 libcommons-collections-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-collections-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-pool-java:
 libcommons-pool-java depends on kaffe | java1-runtime | java2-runtime; however:
  Package kaffe is not installed.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-pool-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtomcat5.5-java:
 libtomcat5.5-java depends on libcommons-dbcp-java; however:
  Package libcommons-dbcp-java is not configured yet.
 libtomcat5.5-java depends on libcommons-el-java; however:
  Package libcommons-el-java is not configured yet.
 libtomcat5.5-java depends on libcommons-logging-java; however:
  Package libcommons-logging-java is not configured yet.
 libtomcat5.5-java depends on libcommons-modeler-java (>= 2.0); however:
  Package libcommons-modeler-java is not configured yet.
 libtomcat5.5-java depends on libcommons-pool-java; however:
  Package libcommons-pool-java is not configured yet.
dpkg: error processing libtomcat5.5-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblog4j1.2-java:
 liblog4j1.2-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing liblog4j1.2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjaxp1.3-java:
 libjaxp1.3-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libjaxp1.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-digester-java:
 libcommons-digester-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 libcommons-digester-java depends on libcommons-beanutils-java (>= 1.7-1); however:
  Package libcommons-beanutils-java is not configured yet.
 libcommons-digester-java depends on libcommons-logging-java; however:
  Package libcommons-logging-java is not configured yet.
dpkg: error processing libcommons-digester-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgcj8-dev:
 libgcj8-dev depends on gcj-4.2 (= 4.2.4-1ubuntu2); however:
  Package gcj-4.2 is not configured yet.
dpkg: error processing libgcj8-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gjdoc:
 gjdoc depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 gjdoc depends on antlr; however:
  Package antlr is not configured yet.
dpkg: error processing gjdoc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ant:
 ant depends on java-gcj-compat-dev | java-virtual-machine; however:
  Package java-gcj-compat-dev is not configured yet.
  Package java-virtual-machine is not installed.
  Package gij which provides java-virtual-machine is not configured yet.
  Package java-gcj-compat which provides java-virtual-machine is not configured yet.
  Package java-gcj-compat-headless which provides java-virtual-machine is not configured yet.
  Package gij-4.2 which provides java-virtual-machine is not configured yet.
 ant depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing ant (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmx4j-java:
 libmx4j-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 libmx4j-java depends on liblog4j1.2-java; however:
  Package liblog4j1.2-java is not configured yet.
dpkg: error processing libmx4j-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libregexp-java:
 libregexp-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libregexp-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblucene-java:
 liblucene-java depends on java-gcj-compat | java2-runtime | java1-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
dpkg: error processing liblucene-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.3-java:
 libservlet2.3-java depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libservlet2.3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libservlet2.4-java:
 libservlet2.4-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libservlet2.4-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libjsch-java:
 libjsch-java depends on java-gcj-compat | java-virtual-machine; however:
  Package java-gcj-compat is not configured yet.
  Package java-virtual-machine is not installed.
  Package gij which provides java-virtual-machine is not configured yet.
  Package java-gcj-compat which provides java-virtual-machine is not configured yet.
  Package java-gcj-compat-headless which provides java-virtual-machine is not configured yet.
  Package gij-4.2 which provides java-virtual-machine is not configured yet.
dpkg: error processing libjsch-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxerces2-java:
 libxerces2-java depends on gij | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package gij is not configured yet.
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 libxerces2-java depends on libjaxp1.3-java; however:
  Package libjaxp1.3-java is not configured yet.
dpkg: error processing libxerces2-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-collections3-java:
 libcommons-collections3-java depends on kaffe (>= 2:1.1.5-3) | java-gcj-compat | java1-runtime | java2-runtime; however:
  Package kaffe is not installed.
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
dpkg: error processing libcommons-collections3-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eclipse-platform:
 eclipse-platform depends on java-gcj-compat | java1-runtime | java2-runtime; however:
  Package java-gcj-compat is not configured yet.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 eclipse-platform depends on libjsch-java (>= 0.1.36); however:
  Package libjsch-java is not configured yet.
 eclipse-platform depends on liblucene-java (>= 1.4.2); however:
  Package liblucene-java is not configured yet.
 eclipse-platform depends on libtomcat5.5-java; however:
  Package libtomcat5.5-java is not configured yet.
dpkg: error processing eclipse-platform (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcommons-launcher-java:
 libcommons-launcher-java depends on kaffe (>= 2:1.1.5-3) | java1-runtime | java2-runtime; however:
  Package kaffe is not installed.
  Package java1-runtime is not installed.
  Package java-gcj-compat which provides java1-runtime is not configured yet.
  Package java2-runtime is not installed.
  Package java-gcj-compat which provides java2-runtime is not configured yet.
 libcommons-launcher-java depends on libcommons-collections-java; however:
  Package libcommons-collections-java is not configured yet.
 libcommons-launcher-java depends on libcommons-logging-java; however:
  Package libcommons-logging-java is not configured yet.
dpkg: error processing libcommons-launcher-java (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eclipse-cdt:
 eclipse-cdt depends on eclipse-platform (>= 3.2.1); however:
  Package eclipse-platform is not configured yet.
dpkg: error processing eclipse-cdt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbcel-java:
 libbcel-java depends on libregexp-java; however:
  Package libregexp-java is not configured yet.
dpkg: error processing libbcel-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gij-4.2
 libecj-java-gcj
 java-gcj-compat-headless
 gcj-4.2
 gappletviewer-4.2
 java-gcj-compat
 ecj
 libcommons-el-java
 libcommons-dbcp-java
 ecj-gcj
 gij
 libcommons-modeler-java
 libcommons-logging-java
 java-gcj-compat-dev
 antlr
 libcommons-beanutils-java
 libcommons-collections-java
 libcommons-pool-java
 libtomcat5.5-java
 liblog4j1.2-java
 libjaxp1.3-java
 libcommons-digester-java
 libgcj8-dev
 gjdoc
 ant
 libmx4j-java
 libregexp-java
 liblucene-java
 libservlet2.3-java
 libservlet2.4-java
 libjsch-java
 libxerces2-java
 libcommons-collections3-java
 eclipse-platform
 libcommons-launcher-java
 eclipse-cdt
 libbcel-java
vivek@vivek-desktop:~$

---

### Post by vivek1985 on 2008-10-02
> **oldos2er said:**
> Could you please copy and paste the output of "cat /etc/apt/sources.list"?
vivek@vivek-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy restricted main universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates restricted main universe multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main universe multiverse #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main universe multiverse #Added by software-properties
vivek@vivek-desktop:~$

---

### Post by oldos2er on 2008-10-02
You should enable the "partner" repository. Go to System, Administration, Software Sources, nad make sure all the boxes are ticked. Reload, and try again.

---

### Post by vivek1985 on 2008-10-02
> **oldos2er said:**
> You should enable the "partner" repository. Go to System, Administration, Software Sources, nad make sure all the boxes are ticked. Reload, and try again.
All the boxes were ticked. All the repositories have been enabled. Even then i am getting the error.

---

### Post by oldos2er on 2008-10-03
Your sources.list shows the partner repository disabled. Run "gksu gedit /etc/apt/sources.list" in a terminal, and uncomment (remove the # from) these two lines: 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

 Save the file, exit, and in the terminal run "sudo aptitude update".

---

### Post by vivek1985 on 2008-10-04
> **oldos2er said:**
> Your sources.list shows the partner repository disabled. Run "gksu gedit /etc/apt/sources.list" in a terminal, and uncomment (remove the # from) these two lines: 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

 Save the file, exit, and in the terminal run "sudo aptitude update".
I ran the commands as u instructed. Those to lines were not commented. I,then executed sudo aptitude update.

Still I am getting the same error.

---

