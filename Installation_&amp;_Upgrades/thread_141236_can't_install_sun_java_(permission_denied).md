---
title: "can't install sun java (permission denied)"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2006-03-07
I was using this guide: [https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca) to install sun's java (to test whether firefox will get faster with that one, if you're curious). I did
```

sudo apt-get install fakeroot java-package java-common
chmod +x jre-1_5_0_06-linux-i586.bin
DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin

```
And I got a long list of permission errors:
```

Creating jre1.5.0_06/lib/javaws.jar
Creating jre1.5.0_06/lib/deploy.jar
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 285: /etc/mailcap: Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrast/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrastInverse/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/LowContrast/48x48/apps': Permission denied
cp: cannot create regular file `/usr/share/pixmaps/sun-java.png': Permission denied
cp: cannot create regular file `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': No such file or directory
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 433: /usr/share/mime-info/java-archive.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 434: /usr/share/mime-info/java-archive.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 435: /usr/share/mime-info/java-archive.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 436: /usr/share/mime-info/java-archive.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 437: /usr/share/mime-info/java-archive.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 438: /usr/share/mime-info/java-archive.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 441: /usr/share/mime-info/java-archive.mime: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 442: /usr/share/mime-info/java-archive.mime: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 445: /usr/share/application-registry/java-archive.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 446: /usr/share/application-registry/java-archive.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 447: /usr/share/application-registry/java-archive.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 448: /usr/share/application-registry/java-archive.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 449: /usr/share/application-registry/java-archive.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 450: /usr/share/application-registry/java-archive.applications: Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrast/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/HighContrastInverse/48x48/apps': Permission denied
mkdir: cannot create directory `/usr/share/icons/LowContrast/48x48/apps': Permission denied
cp: cannot create regular file `/usr/share/pixmaps/sun-java.png': Permission denied
cp: cannot create regular file `/usr/share/icons/HighContrast/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/HighContrastInverse/48x48/apps/sun-java.png': No such file or directory
cp: cannot create regular file `/usr/share/icons/LowContrast/48x48/apps/sun-java.png': No such file or directory
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 433: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 434: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 435: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 436: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 437: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 438: /usr/share/mime-info/java-web-start.keys: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 441: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 442: /usr/share/mime-info/java-web-start.mime: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 445: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 446: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 447: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 448: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 449: /usr/share/application-registry/java-web-start.applications: Permission denied
/home/username/Downloads/jre-1_5_0_06-linux-i586.bin: line 450: /usr/share/application-registry/java-web-start.applications: Permission denied

Done.

Testing extracted archive... okay.

Create debian package:
    dh_testdir
    dh_testroot
    dh_installchangelogs
dh_installchangelogs:

Aborted (dh_installchangelogs).

Removing temporary directory: done

```
There is no .deb packages...

I tried 
```

chmod -R +w /usr/share
``` but it didn't help, gave same errors. Wtf am I doing wrong? 
thanks.

---

### Post by WelterPelter on 2006-03-07
I installed the same thing (well, actually the jdk) earlier today and it worked fine. The only difference I can see is that I used the UI properties window to change the permissions. I doubt that would make any difference, though. I got a few of those errors, but just the ones the guide says to ignore. Sure enough, they didn't seem to matter at all. What does the log file say?

---

### Post by towsonu2003 on 2006-03-07
there is no log file... it erased everything except itself...

---

### Post by towsonu2003 on 2006-03-07
is it possible I installed sun java 1.4 (without deb package) and don't remember about it? Could it mess things up? I've got these options:
```
~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number:
```If that j2se/1.4 is sun's java, is it easy to uninstall it[1]? 

[1]I'll reset the system and build from scratch (partitions, OSes and everything) in three months)...

---

### Post by towsonu2003 on 2006-03-08
bump

---

