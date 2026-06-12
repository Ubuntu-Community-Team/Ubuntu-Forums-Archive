---
title: "Servers down?"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by Ellidi on 2006-08-08
This is a bit annoying. Are the servers simply down or is there a deeper explanation ?

```
$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert
Suggested packages:
  apache2-doc lynx www-browser
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert
0 upgraded, 6 newly installed, 0 to remove and 3 not upgraded.
Need to get 1257kB of archives.
After unpacking 4375kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libapr0 ssl-cert apache2-utils apache2-common apache2-mpm-worker apache2
Install these packages without verification [y/N]? y
Err http://security.ubuntu.com dapper-security/main libapr0 2.0.55-4ubuntu2.1
  Connection failed [IP: 82.211.81.151 80]
Err http://security.ubuntu.com dapper-security/main apache2-utils 2.0.55-4ubuntu2.1
  Connection failed [IP: 82.211.81.151 80]
Err http://security.ubuntu.com dapper-security/main apache2-common 2.0.55-4ubuntu2.1
  Connection failed [IP: 82.211.81.151 80]
Err http://security.ubuntu.com dapper-security/main apache2-mpm-worker 2.0.55-4ubuntu2.1
  Connection failed [IP: 82.211.81.151 80]
Err http://security.ubuntu.com dapper-security/main apache2 2.0.55-4ubuntu2.1
  Connection failed [IP: 82.211.81.151 80]
Err http://au.archive.ubuntu.com dapper/main ssl-cert 1.0.13
  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/libapr0_2.0.55-4ubuntu2.1_i386.deb  Connection failed [IP: 82.211.81.151 80]
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.13_all.deb  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.0.55-4ubuntu2.1_i386.deb  Connection failed [IP: 82.211.81.151 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-common_2.0.55-4ubuntu2.1_i386.deb  Connection failed [IP: 82.211.81.151 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-mpm-worker_2.0.55-4ubuntu2.1_i386.deb  Connection failed [IP: 82.211.81.151 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2_2.0.55-4ubuntu2.1_i386.deb  Connection failed [IP: 82.211.81.151 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Thank you, Ellidi.

---

### Post by Aaron_user on 2006-08-08
I am experiencing this problem also.   Just installed and can't get any updates.   I can browse the repos but the update/install won't work.   Anyone have any ideas?

---

### Post by Ellidi on 2006-08-10
Ok, so I gather that the servers aren't down and this is
a config problem or something in that direction.

Guess it was bit premature to blame the servers right away..

But I still don't know what to do about this.. 

Anyone?

---

### Post by m68k on 2006-08-10
I had the same problem, and solved it by changing the /etc/apt/apt.conf file:

sudo gedit /etc/apt/apt.conf

from:
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";

to:
APT::Authentication::TrustCDROM "true";
Acquire::http::DIRECT;

now everything works fine for me. Maybe the installer detects that I'm behind a proxy, but I'm not. But don't ask me details, I'm quite new to linux.

edit: remove stupid smilies

---

### Post by Ellidi on 2006-08-11
This fixed the problem!
Oh thank you thank you!

Wonder why Ubuntu all of a sudden thought I was behind a proxy...

---

