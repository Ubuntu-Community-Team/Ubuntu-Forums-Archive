---
title: "Unable to install java 1.7 after upgrading to ubuntu 12.04"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by BalaViknesh on 2012-05-07
Hi,

I recently upgraded my machine from ubuntu 11.10 to 12.04.. Everything went smooth except for java 1.7 installation.. 

can anyone help me to resolve with this.. 


Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


From ubuntu software center java is marked as installation completed successfully.

---

### Post by zvacet on 2012-05-08
```
sudo dpkg --configure -a
```

---

### Post by jelabarre on 2012-05-09
> **zvacet said:**
> ```
sudo dpkg --configure -a
```
Nope, because the download package that goes *WITH* the installer is broken.  Rerunning the configuration just fails with same message.

---

### Post by QIII on 2012-05-09
Are you running this from Webupd8's PPA, which can be found on Launchpad and added to your sources.list?

[https://launchpad.net/~webupd8team/+archive/java]("https://launchpad.net/%7Ewebupd8team/+archive/java")

BTW, the current update is u4.

---

