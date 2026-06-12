---
title: "apt-get update not able to get repositories"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by neilbmehta on 2007-06-17
I have just installed Ubuntu (dapper) and was attempting to update using synaptice (and apt-get) howver it was unable to find any of the repositories I believe it is having a problem resolving the url. 
My internet connection is through the net-gear wgr614 v6. My internet connection works fine as shown by the ifconfig file below.

eth0      Link encap:Ethernet  HWaddr 00:01:03:1E:66:C4
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4950 errors:0 dropped:0 overruns:1 frame:0
          TX packets:3569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6348368 (6.0 MiB)  TX bytes:364177 (355.6 KiB)
          Interrupt:11 Base address:0x6000

The command sudo apt-get update gives the following result. 

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg
  Connection failed [IP: 88.198.37.77 80]
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 91.189.89.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
  Connection failed [IP: 88.198.37.77 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
  Connection failed [IP: 81.169.138.125 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 91.189.89.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 91.189.89.6 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 91.189.88.31 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
  Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 91.189.89.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://packages.medibuntu.org/dists/dapper/Release.gpg](http://packages.medibuntu.org/dists/dapper/Release.gpg)  Connection failed [IP: 88.198.37.77 80]
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.medibuntu.org/dists/dapper/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/dapper/free/binary-i386/Packages.gz)  Connection failed [IP: 88.198.37.77 80]
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 91.189.88.31 80]Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failedFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://packages.medibuntu.org/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/dapper/non-free/binary-i386/Packages.gz)  Connection failed [IP: 81.169.138.125 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Connection failedFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Connection failed [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Connection failed [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Connection failed
Reading package lists... Done

Any help would be apreciated. Thanks.

---

### Post by zvacet on 2007-06-18
```
sudo aptitude update
```

or try this

[http://ubuntuforums.org/showthread.php?t=476702]("http://ubuntuforums.org/showthread.php?t=476702")

---

