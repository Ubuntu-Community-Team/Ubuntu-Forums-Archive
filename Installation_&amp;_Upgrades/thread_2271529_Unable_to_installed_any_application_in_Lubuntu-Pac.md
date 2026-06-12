---
title: "Unable to installed any application in Lubuntu-Pacakage operation failed"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by im.saravanan on 2015-03-30
I installed Lubuntu on my Acer AOD 250 netbook. The problem started when i tried to install icedtea-plugin, the package operation failed. Thereafter any package installationa get failed with the following error info.

```
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Selecting previously unselected package p7zip-full. 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 137892 files and directories currently installed.) 
Preparing to unpack .../p7zip-full_9.20.1~dfsg.1-4.1_i386.deb ... 
Unpacking p7zip-full (9.20.1~dfsg.1-4.1) ... 
Processing triggers for man-db (2.7.0.2-2) ... 
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
dpkg: dependency problems prevent configuration of icedtea-plugin: 
 icedtea-plugin depends on icedtea-7-plugin; however: 
  Package icedtea-7-plugin:i386 is not configured yet. 
 
dpkg: error processing package icedtea-plugin (--configure): 
 dependency problems - leaving unconfigured 
Setting up p7zip-full (9.20.1~dfsg.1-4.1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 icedtea-netx:i386 
 icedtea-7-plugin:i386 
 icedtea-plugin 
Error in function:  
Setting up icedtea-netx:i386 (1.5.1-1ubuntu1) ... 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken 
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link 
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken 
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link 
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-i386/jre/bin/javaws doesn't exist 
dpkg: error processing package icedtea-netx:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
```

Need help.....

---

### Post by kerry_s on 2015-03-30
in terminal-> sudo apt-get -f install

---

### Post by im.saravanan on 2015-03-30
thanks for the reply. this is the output

ims@ims-Aspire-one:~$ sudo apt-get -f install 
[sudo] password for ims: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
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
dpkg: dependency problems prevent configuration of icedtea-plugin:
 icedtea-plugin depends on icedtea-7-plugin; however:
  Package icedtea-7-plugin:i386 is not configured yet.

dpkg: error processing package icedtea-plugin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
               Errors were encountered while processing:
 icedtea-netx:i386
 icedtea-7-plugin:i386
 icedtea-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
ims@ims-Aspire-one:~$

---

### Post by kerry_s on 2015-03-30
sudo apt-get purge icedtea-netx icedtea-7-plugin icedtea-plugin
sudo apt-get install icetea-plugin

---

### Post by im.saravanan on 2015-03-31
sorry for the delay, the output of the above code is

ims@ims-Aspire-one:~$     sudo apt-get purge icedtea-netx icedtea-7-plugin icedtea-plugin
[sudo] password for ims: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea-7-plugin* icedtea-netx* icedtea-plugin*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 944 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 137956 files and directories currently installed.)
Removing icedtea-plugin (1.5.1-1ubuntu1) ...
Removing icedtea-7-plugin:i386 (1.5.1-1ubuntu1) ...
Removing icedtea-netx:i386 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-i386/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
Processing triggers for man-db (2.7.0.2-2) ...
ims@ims-Aspire-one:~$ sudo apt-get install icetea-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package icetea-plugin
ims@ims-Aspire-one:~$

---

### Post by im.saravanan on 2015-03-31
I also tried this

ims@ims-Aspire-one:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea-netx-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,350 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 137926 files and directories currently installed.)
Removing icedtea-netx-common (1.5.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
ims@ims-Aspire-one:~$ sudo apt-get install icetea-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package icetea-plugin

---

### Post by kerry_s on 2015-03-31
my bag, typo forgot the "d"

sudo apt-get install icedtea-plugin

---

