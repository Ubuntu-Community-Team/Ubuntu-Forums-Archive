---
title: "Oracle 9i installation on Ubuntu ."
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by saket bansal on 2008-11-17
Hi all,
I have installed VMware server platform on my MS Vista(Bussiness). I am using Ubuntu on VMWare server.On ubuntu I am trying to install Oracle 9i(version 9.2.0.4.0).While oracle installation I am facing problem related to library files.The following error occured:-
Initializing Java Virtual machine from /tmp/OraInstall2008-11-16_03-38-23AM/jre/bin/java.Please wait..
/tmp/OraInstall2008-11-16_03-38-23AM/jre/bin/i386/native_threads/java : error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared obbject file:No such file or directory.

To find a solution I have tried following up some threads on miscellaneous forums.The common solution I see is to install some library packages(using apt-get utility) and then create a softlink to the installed file....Now the problem is that the said library packages are not getting installed.The following error comes:
reading package lists..Done
Building dependency tree
Reading state information...Done
E: Couldn't find package libstdc++2.10-dbg

Please help with a detailed and stepwise solution.Thanks in advance.:)

---

### Post by saket bansal on 2008-11-18
sorry for *bump*

---

### Post by pvella on 2008-11-18
Try running 

apt-cache search libstdc

what is the output?

You might have to run 

apt-get install [package-name]

for the missing packages and might have to add more sources to get the packages that you want.

I am gonna ask a stupid question.  Why do you want to install Oracle 9i?  It is getting pretty old.  If you just need an Oracle Database for development purposes or for education purposes, I would install Oracle Express and there is a really good ubuntu guide here

[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

or there is this guide for installing Oracle Enterprise edition on Ubuntu

[http://t-a-w.blogspot.com/2007/11/installing-oracle-10g-enterprise.html](http://t-a-w.blogspot.com/2007/11/installing-oracle-10g-enterprise.html)

I have the XE version installed on my Ubuntu and it works really well for testing and development purposes and it has a smaller footprint.

Good Luck with the installation. :)

---

### Post by saket bansal on 2008-11-18
> **pvella said:**
> Try running 

apt-cache search libstdc

what is the output?

You might have to run 

apt-get install [package-name]

for the missing packages and might have to add more sources to get the packages that you want.

I am gonna ask a stupid question.  Why do you want to install Oracle 9i?  It is getting pretty old.  If you just need an Oracle Database for development purposes or for education purposes, I would install Oracle Express and there is a really good ubuntu guide here

[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

or there is this guide for installing Oracle Enterprise edition on Ubuntu

[http://t-a-w.blogspot.com/2007/11/installing-oracle-10g-enterprise.html](http://t-a-w.blogspot.com/2007/11/installing-oracle-10g-enterprise.html)

I have the XE version installed on my Ubuntu and it works really well for testing and development purposes and it has a smaller footprint.

Good Luck with the installation. :)


Hi,
Thanks for your reply..
Going by your suggestion I have started with installation of Oracle Express.Now the problem is that I am not able to configure it.Neither of the process is showing "Done" status and neither of the process nor any of the variable is getting initialized.
While tryin to reconfigure it using command
$/etc/init.d/oracle-xe configure
it gives me the prompt "Oracle Database 10G Express Edition already configured"

Also neither of the database files have been created.

Please help with configuration..

---

