---
title: "Errors were encountered while processing: icedtea-netx:i386"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by shamsat on 2014-12-22
I get this error in ubuntu 14.10, i run the apt-get update and apt-get -f install but no one fix this problem, this is the error:
> 
# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of icedtea-7-plugin:i386:
 icedtea-7-plugin:i386 depends on icedtea-netx (= 1.5.1-1ubuntu1); however:
  Package icedtea-netx:i386 is not configured yet.

dpkg: error processing package icedtea-7-plugin:i386 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 icedtea-netx:i386
 icedtea-7-plugin:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by schragge on 2014-12-23
Please post the output of following commands:
```

update-alternatives --display itweb-settings
update-alternatives --display javaws
update-alternatives --display java

```

Also have a look at [thread=2257931]this thread[/thread].

---

### Post by shamsat on 2014-12-26
Thanks for reply:
> 
# update-alternatives --display itweb-settings
itweb-settings - auto mode
  link currently points to /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/itweb-settings - priority 1061
  slave itweb-settings.1.gz: /usr/lib/jvm/java-6-openjdk-i386/jre/man/man1/itweb-settings.1.gz
/usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings - priority 1071
  slave itweb-settings.1.gz: /usr/lib/jvm/java-7-openjdk-i386/jre/man/man1/itweb-settings.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings'.


> 
#update-alternatives --display javaws
javaws - auto mode
  link currently points to /usr/lib/jvm/java-7-openjdk-i386/jre/bin/javaws
/usr/lib/jvm/java-6-openjdk-i386/jre/bin/javaws - priority 1061
  slave javaws.1.gz: /usr/lib/jvm/java-6-openjdk-i386/jre/man/man1/javaws.1.gz
/usr/lib/jvm/java-7-openjdk-i386/jre/bin/javaws - priority 1071
  slave javaws.1.gz: /usr/lib/jvm/java-7-openjdk-i386/jre/man/man1/javaws.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-openjdk-i386/jre/bin/javaws'.


> 
# update-alternatives --display java
java - auto mode
  link currently points to /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
/usr/bin/gij-4.9 - priority 1049
  slave java.1.gz: /usr/share/man/man1/gij-4.9.1.gz
/usr/lib/jvm/java-7-openjdk-i386/jre/bin/java - priority 1071
  slave java.1.gz: /usr/lib/jvm/java-7-openjdk-i386/jre/man/man1/java.1.gz
Current 'best' version is '/usr/lib/jvm/java-7-openjdk-i386/jre/bin/java'.


---

### Post by mörgæs on 2014-12-26
For posting terminal output please use CODE and not QUOTE tags.

---

### Post by Bucky Ball on 2014-12-26
> **mörgæs said:**
> For posting terminal output please use CODE and not QUOTE tags.

See the last link in my signature for how to. ;)

---

### Post by schragge on 2014-12-26
It's LP #[lpbug]1363785[/lpbug] aka debbugs #[759226]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=759226"). Solutions, in order of preference:

**1.** It's already fixed in  *icedtea-netx* 1.5.2 available from **utopic-proposed** repository. See [uwiki]Testing/EnableProposed[/uwiki] for how to enable it and install packages from there. The instruction is for trusty. Everywhere it says trusty just replace it with utopic.

**2.** Replace the file */var/lib/dpkg/info/icedtea-netx:i386.postinst* with that from package *icedtea-netx* 1.5.2. Download [ATTACH]258803[/ATTACH], then in terminal
```

tar xvf ~/Downloads/icedtea-netx-i386-postinst-fixed.tar.gz
sudo cp -v icedtea-netx*.postinst /var/lib/dpkg/info/
sudo dpkg --configure -a

```

**3.** Alternatively, you can use this dirty hack to make apt-get happy ([suggested by Allan Bruno Petersen aka metalight]("https://answers.launchpad.net/ubuntu/+source/icedtea-web/+question/254216")):
```

sudo ln -sv /usr/lib/jvm/java-{7,8}-openjdk-i386
sudo apt-get install -f

```

---

