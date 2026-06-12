---
title: "Can't remove/upgrade git-daemon-sysvinit"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by amigabill2 on 2014-03-23
I'm having problems doing some uprade, involving git-daemon-sysvinit. It seems stuck. I am having trouble adding other items due to this.


sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  git-daemon-sysvinit
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 573 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 298037 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)




sudo apt-get remove git-daemon-sysvinit
After this operation, 573 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 298037 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)



sudo dpkg --remove git-daemon-sysvinit
(Reading database ... 298037 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit



sudo dpkg --remove --force-all git-daemon-sysvinit
(Reading database ... 298037 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit

---

### Post by Kirboosy on 2014-03-24
Welcome to the forums! :D

What happens when you run the following command?

```
sudo apt-get install -f
```

Hope that helps!
~Caboose
PS Please use the [CODE] tags when submitting terminal outputs or commands. It makes it much more readable. If you go advanced edit you can click the ***#*** button to show the code brackets

---

### Post by amigabill2 on 2014-03-24
> **Caboose885 said:**
> Welcome to the forums! :D

What happens when you run the following command?

```
sudo apt-get install -f
```

Hope that helps!
~Caboose
PS Please use the ```
 tags when submitting terminal outputs or commands. It makes it much more readable. If you go advanced edit you can click the ***#*** button to show the code brackets

[code]
sudo apt-get install -f
[sudo] password for billt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ant ant-optional antlr3 apache2-utils aspectj bsh bsh-gcj default-jdk-doc
  gcj-4.8-jre-lib javahelp2 jetty jsvc junit junit-doc junit4 junit4-doc libantlr-java
  libapache-pom-java libapr1 libaprutil1 libasm3-java libaspectj-java
  libbeansbinding-java libbetter-appframework-java libbindex-java libbytelist-java
  libcglib-java libcommons-beanutils-java libcommons-codec-java
  libcommons-collections3-java libcommons-compress-java libcommons-daemon-java
  libcommons-digester-java libcommons-logging-java libcommons-net1-java
  libcommons-parent-java libdb-java libdb-je-java libdb5.1-java libdb5.1-java-jni
  libeasymock-java libexpat1:i386 libfelix-framework-java libfelix-main-java
  libflute-java libfontconfig1:i386 libfreemarker-java libfreetype6:i386 libgcj-bc
  libgcj-common libgcj14 libgeronimo-jpa-2.0-spec-java libgeronimo-osgi-support-java
  libhamcrest-java libhamcrest-java-doc libicu4j-java libini4j-java libjcodings-java
  libjemmy2-java libjetty-java libjline-java libjna-java libjoda-convert-java
  libjoda-time-java libjsch-java libjtidy-java libjvyamlb-java libjzlib-java
  liblucene2-java libmysql-java libnb-absolutelayout-java libnb-apisupport3-java
  libnb-ide14-java libnb-java5-java libnb-javaparser-java
  libnb-org-openide-modules-java libnb-org-openide-util-java
  libnb-org-openide-util-lookup-java libnb-platform-devel-java libnb-platform13-java
  libnetx-java liboro-java libosgi-compendium-java libosgi-core-java
  libosgi-foundation-ee-java libpostgresql-jdbc-java libregexp-java libsac-java
  libsac-java-gcj libsequence-library-java libserf1 libservlet2.5-java
  libsimple-validation-java libslf4j-java libsqljet-java libssl1.0.0:i386
  libstdc++6:i386 libstringtemplate-java libsvn-java libsvn1 libsvnclientadapter-java
  libsvnkit-java libswing-layout-java libswingx1-java libtrilead-ssh2-java
  libx11-6:i386 libxau6:i386 libxcb1:i386 libxcursor1:i386 libxdmcp6:i386
  libxerces2-java libxext6:i386 libxfixes3:i386 libxi6:i386
  libxml-commons-external-java libxml-commons-resolver1.1-java libxrandr2:i386
  libxrender1:i386 libxz-java linux-headers-3.11.0-13 linux-headers-3.11.0-13-generic
  linux-image-3.11.0-13-generic linux-image-extra-3.11.0-13-generic openjdk-6-jdk
  openjdk-7-doc openjdk-7-jre-lib tk8.6-lib
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  git-daemon-sysvinit
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 573 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 298037 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemoem,n-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'd installed a bunch of those can be removed items trying to build the newest Octave version, and guess I can let most of that go as someone else will surely make a package before I get it working myself. 

A few items I will need to keep around for other non-apt software.

---

### Post by Kirboosy on 2014-03-25
```
sudo apt-get autoclean
```
```
sudo dpkg --purge --force-remove-reinstreq git-daemon-sysvinit
```

Here is what I'm doing (I copied this straight out of the man page for dpkg.

> 

**--purge**  removes  everything,  including conffiles. If -a or
              --pending is given instead of a package name, then all  packages
              unpacked,   but   marked   to  be  removed  or  purged  in  file
              _/var/lib/dpkg/status_, are removed or purged, respectively.

**reinst-required**
              A  package  marked  reinst-required  is  broken   and   requires
              reinstallation.  These packages cannot be removed, unless forced
              with option **--force-remove-reinstreq**. 

What were you doing when the package got stuck initially?

Hope that helps!
~Caboose

---

### Post by amigabill2 on 2014-03-29
> **Caboose885 said:**
> ```
sudo apt-get autoclean
```  ```
sudo apt-get autoclean Reading package lists... Done Building dependency tree        Reading state information... Done
```  > ```
sudo dpkg --purge --force-remove-reinstreq git-daemon-sysvinit
```  ```
sudo dpkg --purge --force-remove-reinstreq git-daemon-sysvinit(Reading database ... 298037 files and directories currently installed.) Removing git-daemon-sysvinit ... update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force) dpkg: error processing git-daemon-sysvinit (--purge):  subprocess installed post-removal script returned error exit status 1 Processing triggers for ureadahead ... Errors were encountered while processing:  git-daemon-sysvinit 
```  > What were you doing when the package got stuck initially? I was trying to install something, what exactly I now forget. Some of these git things came up as recommended installs to go with whatever I was after at the time, and so I went to do them too after my initial qpt-get isntall finished. This git-daemon-sysvinit I believe was one of those, and now I wish I had not gone for them too.

---

