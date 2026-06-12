---
title: "jdk1.6.0_29 for ubuntu 11.10"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by princebadshah on 2011-12-30
Hi Geeks

I am unable to install  jdk1.6.0_29 version of java ....
I installed 7 before but now i uninstalled it through software centre ...

i tried this
 
root@ubuntu:/home/elysium# sudo apt-get install sun-java6-jre sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-jdk' has no installation candidate

---

### Post by Karlchen on 2011-12-30
Hello, princebadshah.

I am not 100% sure that previous Java versions before v1.6_30 are affected as well. But the symptoms you describe might suggest they are:

Oracle has revoked the license from all Linux distributions to repackage the original Java installation packages provided by Oracle as .DEB or .RPM packages and offer them in their own repositories.
As a consquence Canonical is no longer allowed to offer Oracle JRE or Oracle JDK packages for download and installation.
Yet, Oracle generously permits you to download JRE/JDK packages from the Oracle Java download pages and install them yourself.
In case you wish to do so, please, check out this step by step instruction: [**Oracle (Sun) Java JRE for Ubuntu, Linux Mint and Debian**]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY")

Kind regards,
Karl

---

### Post by ebasa on 2011-12-30
Sun java has been removed, so you must use the files from Sun if you want real java.

Excellent instructions here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by princebadshah on 2011-12-30
I followed this tutorial

[LIST=1]
[*]Download [Java SE 6 JDK]("http://www.oracle.com/technetwork/java/javase/downloads/index.html") for Linux x86 self-extracting binary
[*]From the download folder, make the file executable
chmod a+x jdk-6u*<version>*-linux-i586.bin
[*]Move the file to the jvm folder
sudo mv jdk-6u*<version>*-linux-i586.bin /usr/lib/jvm/
[*]Change to the jvm folder and run the self-extracting binary
cd /usr/lib/jvm
sudo ./jdk-6u*<version>*-linux-i586.bin
Everything will be extracted to a new jdk1.6*<version>* folder and you can delete the .bin file now.
[/LIST]


But get these errors ..!!! 

root@ubuntu:/home/elysium# sudo ln -s -b jdk1.6.0_29/jre/bin/java /etc/alternatives/java
root@ubuntu:/home/elysium# java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: apt-get install <selected package>
root@ubuntu:/home/elysium# /etc/alternatives/java -version
bash: /etc/alternatives/java: No such file or directory

---

### Post by Perfect Storm on 2011-12-31
follow the guide that both ebasa and Karlchen posted instead.

---

