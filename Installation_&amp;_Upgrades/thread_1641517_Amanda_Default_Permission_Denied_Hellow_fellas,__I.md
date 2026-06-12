---
title: "Amanda Default Permission Denied Hellow fellas,  I'm trying to install Amanda 3.2 on"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by glennbilocca on 2010-12-09
Hellow fellas,

I'm trying to install Amanda 3.2 on Ubuntu 10.10(Maverick) using Ubuntu  10.04 deb package. The installation was succesgul using the dpkg  command. The problem crops up when configuring such amanda. When  creating a user amandabackup using passwd amandabackup and then enter in  it through su - amandabackup a permission denied problem comes up. When  enter amserverconfig Dailyset 1 etc etc the server response with :

amservingconfig: critical (fatal): Cannot create debug file  "/var/log/amanda/server/amserverconfig.2010120307947.debug": Permission  denied and continues

The permissions are set to rw 1 amandabackup backup. I can't understand  why it's telling me permission denied each time. It will be a pleasure if  you would help me.

Regards

---

### Post by glennbilocca on 2010-12-09
Hellow fellas,

I'm trying to install Amanda 3.2 on Ubuntu 10.10(Maverick) using Ubuntu  10.04 deb package. The installation was succesgul using the dpkg  command. The problem crops up when configuring such amanda. When  creating a user amandabackup using passwd amandabackup and then enter in  it through su - amandabackup a permission denied problem comes up. When  enter amserverconfig Dailyset 1 etc etc the server response with :

amservingconfig: critical (fatal): Cannot create debug file  "/var/log/amanda/server/amserverconfig.2010120307947.debug": Permission  denied and continues

The permissions are set to rw 1 amandabackup backup. I can't understand  why it's telling me permission denied each time. It will be a pleasure if  you would help me.

Regards

---

### Post by s.fox on 2010-12-09
Please do not create duplicate threads. Thank you.

Threads Merged.

---

### Post by posterlion on 2010-12-27
> **glennbilocca said:**
> amservingconfig: critical (fatal): Cannot create debug file  "/var/log/amanda/server/amserverconfig.2010120307947.debug": Permission  denied and continues
Regards

Login to your amanda server and do this:

michael0@am26:~$ su -
Password:
root@am26:~# cd /var/log/amanda
root@am26:/var/log/amanda# ls -al
total 20
drwxrwx---  4 backup backup 4096 2010-12-24 11:04 .
drwxr-xr-x 10 root   root   4096 2010-12-27 06:27 ..
drwx------  2 backup backup 4096 2010-12-24 11:17 amandad
-rw-r--r--  1 backup backup  637 2010-12-23 17:20 amserverconfig.20101223172022.
debug
drwx------  3 backup backup 4096 2010-12-26 11:55 server
root@am26:/var/log/amanda#

Then post the results.

---

