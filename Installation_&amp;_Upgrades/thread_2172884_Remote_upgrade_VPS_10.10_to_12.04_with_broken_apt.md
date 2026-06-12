---
title: "Remote upgrade VPS 10.10 to 12.04 with broken apt"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by wilson-eric-n on 2013-09-06
I'm trying to install some things on a VPS with 10.10, and having trouble.

For example:

```
$ sudo apt-get install git

[ ... stuff ... ]
WARNING: The following packages cannot be authenticated!
  libcurl3-gnutls libdigest-sha1-perl git
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com/ubuntu/ maverick/main libdigest-sha1-perl amd64 2.13-1
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-security/main libcurl3-gnutls amd64 7.21.0-1ubuntu1.3
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-security/main git amd64 1:1.7.1-1.1ubuntu0.1
  404  Not Found [IP: 91.189.92.202 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.21.0-1ubuntu1.3_amd64.deb  404  Not Found [IP: 91.189.92.202 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libd/libdigest-sha1-perl/libdigest-sha1-perl_2.13-1_amd64.deb  404  Not Found [IP: 91.189.92.202 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/git/git_1.7.1-1.1ubuntu0.1_amd64.deb  404  Not Found [IP: 91.189.92.202 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
If I try:

```
$ sudo apt-get update

```
Then:

```
[ ... stuff ... ]
Err http://archive.ubuntu.com maverick/main amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick/universe amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/main amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/main amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
Err http://archive.ubuntu.com maverick-security/universe amd64 Packages
  404  Not Found [IP: 91.189.92.202 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz  404  Not Found [IP: 91.189.92.202 80]


E: Some index files failed to download, they have been ignored, or old ones used instead.



```

Sources list:


```
$ sudo cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu maverick main restricted universe
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted universe
deb http://archive.ubuntu.com/ubuntu maverick-security main restricted universe



```

I also tried:
```
$ sudo do-release-upgrade -c
sudo: do-release-upgrade: command not found



```
I'm guessing that my problem is related to 10.10 being no longer supported. I'd like to move to 12.04. My understanding is that you can't upgrade skipping versions, except LTS to LTS.

Could someone help me find a path towards a server that is working with 12.04? It doesn't matter if I destroy everything that is currently on the server in the process.

---

### Post by TheFu on 2013-09-07
It is probably easier to install a fresh 12.04 and migrate the apps then to do the 
10.10 --> 11.04 --> 11.10 --> 12.04  updates.

Of course the specific app involved can cause added issues.

I found an app that refused to upgrade because the perl libraries had changed. Had to switch to a different app or spend every patch period fighting with the old app.

At least you are going LTS. Smart move.

---

