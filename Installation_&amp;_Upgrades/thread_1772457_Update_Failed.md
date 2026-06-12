---
title: "Update Failed"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by AnarchistForPrez on 2011-05-31
Hey everybody, jsut logged onto my cpu and saw that i hade updates in the update manager. I tried to run them and they failed, citing that maybe there was an issue with the connection to the internet. Which there isn't.

went into terminal and typed sudo apt-get dist-upgrade and had the same result....


anarchistforprez@Moses:~$ sudo apt-get dist-upgrade
[sudo] password for anarchistforprez: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bind9-host dnsutils gnome-nettool libbind9-60 libdns66 libisc60 libisccc60 libisccfg60 liblwres60 libpam-modules
  libpam-runtime libpam0g
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 512kB/1,815kB of archives.
After this operation, 8,192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main libpam0g i386 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main libpam0g i386 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main libpam-modules i386 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main libpam-runtime all 1.1.1-4ubuntu2.2
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-4ubuntu2.2_i386.deb)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-4ubuntu2.2_i386.deb)  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-4ubuntu2.2_all.deb)  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

tried both of these suggestions and neither worked. any thoughts would be greatly appreciated. thanks in advance.

---

### Post by mikewhatever on 2011-05-31
You should probably try another mirror, or just wait and try again tomorrow.

---

### Post by BlouBlou on 2011-05-31
I'd suggest you using "Main server", it always works perfectly.
Changing server should fix your problem.

---

