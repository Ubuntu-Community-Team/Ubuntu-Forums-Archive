---
title: "Need help upgrading server"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by akaney on 2008-07-01
Hi all,

I am having problems updating my 7.10 to 8.04. I have read and tried a number of posts of people having the same problem as me, but none of their answers work for me.  Here is what I have. 

I tried to upgrade my distribution, and got the following:
sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  e2fslibs e2fsprogs libblkid1 libss2 libuuid1 linux-image-2.6.22-14-server
  openssh-client openssh-server
8 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.1MB of archives. After unpacking 4096B will be freed.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libblkid1 e2fsprogs openssh-client e2fslibs libuuid1
  linux-image-2.6.22-14-server libss2 openssh-server

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main e2fslibs 1.40.2-1ubuntu1.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main e2fsprogs 1.40.2-1ubuntu1.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main linux-image-2.6.22-14-server 2.6.22-14.52
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libblkid1 1.40.2-1ubuntu1.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libss2 1.40.2-1ubuntu1.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libuuid1 1.40.2-1ubuntu1.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main openssh-server 1:4.6p1-5ubuntu0.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main openssh-client 1:4.6p1-5ubuntu0.1
  Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb:) Cannot initiate the connection to security.ubuntu.com:80 (91.189.88.37). - connect (101 Network is unreachable)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

So then I ran through the Ubuntu documentation and got:
 
sudo aptitude install update-manager-core
sudo do-release-upgrade
  Checking for a new ubuntu release
  No new release found

I am really new to this, and am unfamiliar with where to go from here.  Any help would be appreciated

---

