---
title: "Rebuild new deb packages to repository,but wrong to fetch during install"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by yichengli on 2015-11-15
```
root@node-1:/tmp/main# apt-get update
Ign [http://10.60.0.2](http://10.60.0.2) precise Release.gpg
Hit [http://10.60.0.2](http://10.60.0.2) precise Release
Ign [http://10.60.0.2](http://10.60.0.2) precise/main amd64 Packages/DiffIndex
Ign [http://10.60.0.2](http://10.60.0.2) precise/main i386 Packages/DiffIndex
Ign [http://10.60.0.2](http://10.60.0.2) precise/main TranslationIndex
Hit [http://10.60.0.2](http://10.60.0.2) precise/main amd64 Packages
Hit [http://10.60.0.2](http://10.60.0.2) precise/main i386 Packages
Ign [http://10.60.0.2](http://10.60.0.2) precise/main Translation-en_US
Ign [http://10.60.0.2](http://10.60.0.2) precise/main Translation-en
Reading package lists... Done
root@node-1:/tmp/main# apt-get -q -y -o DPkg::Options::=--force-confold --force-yes install python-oslo.messaging=1.4.1-fuel6.0~mira18~tc01
Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be DOWNGRADED:
  python-oslo.messaging
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 86.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  python-oslo.messaging
Authentication warning overridden.
Err [http://10.60.0.2/2014.2-6.0/ubuntu/x86_64/](http://10.60.0.2/2014.2-6.0/ubuntu/x86_64/) precise/main python-oslo.messaging all 1.4.1-fuel6.0~mira18~tc01
  404  Not Found
Failed to fetch [http://10.60.0.2:8080/2014.2-6.0/ubuntu/x86_64/.//python-oslo.messaging_1.4.1-fuel6.0~mira18~tc01_all.deb](http://10.60.0.2:8080/2014.2-6.0/ubuntu/x86_64/.//python-oslo.messaging_1.4.1-fuel6.0~mira18~tc01_all.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@node-1:~# apt-cache policy python-oslo.messaging
python-oslo.messaging:
Installed: 1.4.1-fuel6.0~mira18
Candidate: 1.4.1-fuel6.0~mira18
Version table:
*** 1.4.1-fuel6.0~mira18 0
100 /var/lib/dpkg/status
1.4.1-fuel6.0~mira18~tc01 0
500 [http://10.60.0.2/2014.2-6.0/ubuntu/x86_64/](http://10.60.0.2/2014.2-6.0/ubuntu/x86_64/) precise/main amd64 Packages
```

```
Err [http://10.60.0.2/2014.2-6.0/ubuntu/x86_64/](http://10.60.0.2/2014.2-6.0/ubuntu/x86_64/) precise/main python-oslo.messaging all 1.4.1-fuel6.0~mira18~tc01
  404  Not Found
Failed to fetch [http://10.60.0.2:8080/2014.2-6.0/ubuntu/x86_64/.//python-oslo.messaging_1.4.1-fuel6.0~mira18~tc01_all.deb](http://10.60.0.2:8080/2014.2-6.0/ubuntu/x86_64/.//python-oslo.messaging_1.4.1-fuel6.0~mira18~tc01_all.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

[http://10.60.0.2:8080/2014.2-6.0/ubuntu/x86_64/.//python-oslo.messaging_1.4.1-fuel6.0~mira18~tc01_all.deb](http://10.60.0.2:8080/2014.2-6.0/ubuntu/x86_64/.//python-oslo.messaging_1.4.1-fuel6.0~mira18~tc01_all.deb)     wrong path

---

### Post by Blackbug on 2015-11-15
Please verify the ppa for the package.

---

