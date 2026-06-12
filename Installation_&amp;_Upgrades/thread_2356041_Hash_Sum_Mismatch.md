---
title: "Hash Sum Mismatch"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by murad-mouri on 2017-03-19
I am trying to install following:
apt-get install joe wget p7zip-full curl build-essential zlib1g-dev libcurl4-gnutls-dev in Ubuntu 16.04 LTS running in VMWare workstation with 2GB RAM and 30GB HDD. Have been trying this for last one month, every time I am getting Hash Sum Mismatch in package libisl15 & gcc-5_5.4.0. Can any one please help me how to overcome this issue. My Internet is 4mbps with router for wifi but the VMWare is running in PC with Windows 10.
Please see 
[https://mega.nz/#!n5lziBjR!vMppuQeoGW1AhSFX21cho-0z2F5xpAH3EcRDRwM6rTo](https://mega.nz/#!n5lziBjR!vMppuQeoGW1AhSFX21cho-0z2F5xpAH3EcRDRwM6rTo) image for the output what I am getting.

---

### Post by oldos2er on 2017-03-19
Try ```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

---

### Post by murad-mouri on 2017-03-19
after doing this I got below error:
Err:1 http//us.archive.ubuntu.com/ubuntu xenial/main amd64 libisl15 amd64 0.16.1-1
  Cannot initiate the connection to us.archive.ubuntu.com:80 (20001:67c:1562::16). - connect (101: Network is unreachable) [IP: 20001:67c:1562::16 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/isl/libisl15_0.16.1-1_amd64.dev](http://us.archive.ubuntu.com/ubuntu/pool/main/i/isl/libisl15_0.16.1-1_amd64.dev)
Cannot initiate the connection to us.archive.ubuntu.com:80 (20001:67c:1562::16). - connect (101: Network is unreachable) [IP: 20001:67c:1562::16 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
It's a IP6, do I need any special thing?
on 80% of downloading I got Hash Sum Mismatch

---

