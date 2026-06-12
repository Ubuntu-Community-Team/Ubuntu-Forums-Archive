---
title: "Problems with ca-certificates-java -HELP!"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by _Smiler_ on 2010-07-25
Hi, I performed a fresh install of Ubuntu 9.10 this morning and upgraded to Lucid straight away (after running the Update Manager). I did it this way because I had a 9.10 CD and forgot the newest version was 10.04. My last installation was a dual boot Lucid with XP. I had no problems with this installation (well, loads of problems with XP-reason for fresh install- but none with Lucid). I've encountered various problems - after installing ubuntu-restricted-extras package from the Documentation website, it threw up this error ```
E: ca-certificates-java: subprocess installed post-installation script returned error exit status 139

``` 

Trying to install from the terminal yeilds: ```
toes@toesywoseys:~$ sudo apt-get install ca-certificates-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ca-certificates-java is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 openoffice.org-l10n-en-gb linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ca-certificates-java (20100406ubuntu1) ...
creating /etc/ssl/certs/java/cacerts...
/var/lib/dpkg/info/ca-certificates-java.postinst: line 92:  2612 Segmentation fault      cp /usr/share/ca-certificates-java/cacerts $KEYSTORE
dpkg: error processing ca-certificates-java (--configure):
 subprocess installed post-installation script returned error exit status 139
Errors were encountered while processing:
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've reported a bug too, using the first error (I couldn't find a bug exactly matching)
Here it is: [https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/609818]("https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/609818")

I really don't know what to do here. Please don't tell me I have to sift through music folders again to do a back-up and reinstall!

---

