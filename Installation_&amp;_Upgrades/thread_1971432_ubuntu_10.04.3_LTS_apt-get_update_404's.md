---
title: "ubuntu 10.04.3 LTS apt-get update 404's"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by gmfpanda on 2012-05-02
Hi All,

Getting lots of 404s on apt-get update. here is what I am getting below.  Any help is much appreciated and thanks in advance.

Begin Paste:
--------------------
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_
US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en
_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_U
S
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en
_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_
US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,383kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [415kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,840B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [122kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,259B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [142kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [38.9kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,335B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,349B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,193B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,430kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
  404  Not Found [IP: 91.189.92.166 80]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [176kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [608kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,638B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [221kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [286kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [98.0kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.3kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,565B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
  404  Not Found [IP: 91.189.92.180 80]
Fetched 13.1MB in 6s (2,127kB/s)
root@D18712:~# ~

---

### Post by QIII on 2012-05-02
A quick look gives me the impression that your 404s are coming from Karmic repos, which is not surprizing since Karmic is well past its EOL.

May I ask why you are using a root account?

---

### Post by gmfpanda on 2012-05-02
I was just logged in as root and decided to, is that bad?

---

### Post by QIII on 2012-05-02
There is no root account in Ubuntu by default for security reasons.  Having one is risky and you should only have one if you have a very good reason to.  It might be hard to find that reason.

There is a sticky about it somewhere (I'm on my cell so I can't link it.)

Use sudo to temporarily elevate your priviledges.

---

