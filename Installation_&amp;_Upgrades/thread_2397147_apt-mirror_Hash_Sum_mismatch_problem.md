---
title: "apt-mirror Hash Sum mismatch problem"
date: 2018-07-26
forum: Installation &amp; Upgrades
---

### Post by ashfaqur.rahman on 2018-07-26
Hi

I am running kubuntu (18.04) x64, fully updated.

I maintain a local repository with apt-mirror

part of the apt-mirror config file at /etc/apt/mirror.list looks like this
```

#
deb-amd64 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic main restricted universe multiverse
deb-amd64 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-updates main restricted universe multiverse
deb-amd64 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-security main restricted universe multiverse
deb-amd64 [http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu) bionic-backports main restricted universe multiverse
#
deb-amd64 [http://ppa.launchpad.net/gns3/ppa/ubuntu](http://ppa.launchpad.net/gns3/ppa/ubuntu) bionic main
#
clean [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/)
clean [http://ppa.launchpad.net/ugns3/ppa/ubuntu/](http://ppa.launchpad.net/ugns3/ppa/ubuntu/)
#

```


My /etc/apt/sources.list file looks like this
```

deb [arch=amd64] file:/mnt/UBUNTU-REPO/REPO bionic main restricted universe multiverse
deb [arch=amd64] file:/mnt/UBUNTU-REPO/REPO bionic-updates main restricted universe multiverse
deb [arch=amd64] file:/mnt/UBUNTU-REPO/REPO bionic-backports main restricted universe multiverse
deb [arch=amd64] file:/mnt/UBUNTU-REPO/REPO bionic-security main restricted universe multiverse
deb [arch=amd64] file:/mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu bionic main

```


Things were working fine until now, when I suddenly started to get all sorts of 'Hash Sum mismatch' errors
```

$ sudo sh -c 'apt update && apt upgrade -y && apt autoremove -y && apt clean'

Get:1 file:/mnt/UBUNTU-REPO/REPO bionic InRelease [242 kB]
Get:1 file:/mnt/UBUNTU-REPO/REPO bionic InRelease [242 kB]
Get:2 file:/mnt/UBUNTU-REPO/REPO bionic-updates InRelease [88.7 kB]
Get:3 file:/mnt/UBUNTU-REPO/REPO bionic-backports InRelease [74.6 kB]
Get:4 file:/mnt/UBUNTU-REPO/REPO bionic-security InRelease [83.2 kB]
Get:5 file:/mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu bionic InRelease
Ign:5 file:/mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu bionic InRelease
Get:6 file:/mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu bionic Release
Err:6 file:/mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu bionic Release
  File not found - /mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu/dists/bionic/Release (2: No such file or directory)
Get:2 file:/mnt/UBUNTU-REPO/REPO bionic-updates InRelease [88.7 kB]
Get:3 file:/mnt/UBUNTU-REPO/REPO bionic-backports InRelease [74.6 kB]
Get:4 file:/mnt/UBUNTU-REPO/REPO bionic-security InRelease [83.2 kB]
Get:7 file:/mnt/UBUNTU-REPO/REPO bionic/main amd64 Packages [1,019 kB]
Ign:7 file:/mnt/UBUNTU-REPO/REPO bionic/main amd64 Packages
Get:8 file:/mnt/UBUNTU-REPO/REPO bionic/main Translation-en [516 kB]
Ign:8 file:/mnt/UBUNTU-REPO/REPO bionic/main Translation-en
Get:9 file:/mnt/UBUNTU-REPO/REPO bionic amd64 Contents (deb) [39.5 MB]
Ign:9 file:/mnt/UBUNTU-REPO/REPO bionic amd64 Contents (deb)
Get:10 file:/mnt/UBUNTU-REPO/REPO bionic/main amd64 DEP-11 Metadata [477 kB]
Ign:10 file:/mnt/UBUNTU-REPO/REPO bionic/main amd64 DEP-11 Metadata
Get:11 file:/mnt/UBUNTU-REPO/REPO bionic/restricted amd64 Packages [9,184 B]
Ign:11 file:/mnt/UBUNTU-REPO/REPO bionic/restricted amd64 Packages
Get:12 file:/mnt/UBUNTU-REPO/REPO bionic/restricted Translation-en [3,584 B]
Ign:12 file:/mnt/UBUNTU-REPO/REPO bionic/restricted Translation-en
Get:13 file:/mnt/UBUNTU-REPO/REPO bionic/universe amd64 Packages [8,570 kB]
Ign:13 file:/mnt/UBUNTU-REPO/REPO bionic/universe amd64 Packages
Get:14 file:/mnt/UBUNTU-REPO/REPO bionic/universe Translation-en [4,941 kB]
Ign:14 file:/mnt/UBUNTU-REPO/REPO bionic/universe Translation-en
Get:15 file:/mnt/UBUNTU-REPO/REPO bionic/universe amd64 DEP-11 Metadata [3,287 kB]
Ign:15 file:/mnt/UBUNTU-REPO/REPO bionic/universe amd64 DEP-11 Metadata
Get:16 file:/mnt/UBUNTU-REPO/REPO bionic/multiverse amd64 Packages [151 kB]
Ign:16 file:/mnt/UBUNTU-REPO/REPO bionic/multiverse amd64 Packages
Get:17 file:/mnt/UBUNTU-REPO/REPO bionic/multiverse Translation-en [108 kB]
Ign:17 file:/mnt/UBUNTU-REPO/REPO bionic/multiverse Translation-en
Get:18 file:/mnt/UBUNTU-REPO/REPO bionic/multiverse amd64 DEP-11 Metadata [49.7 kB]
Ign:18 file:/mnt/UBUNTU-REPO/REPO bionic/multiverse amd64 DEP-11 Metadata
Get:7 file:/mnt/UBUNTU-REPO/REPO bionic/main amd64 Packages [1,019 kB]
Get:8 file:/mnt/UBUNTU-REPO/REPO bionic/main Translation-en [516 kB]
Err:8 file:/mnt/UBUNTU-REPO/REPO bionic/main Translation-en                          
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:3166991 [weak]
   - SHA256:d248b4a1ea1d6fca76c1d3cbff6cb7fb3a5d64aa7ad42ff4f6c9e77039ba3be0
   - SHA1:d5dad09520f0a3dc3eea91361c143694568ed854 [weak]
   - MD5Sum:d88743a10ec2a2bcaa5980711ce7920b [weak]
  Hashes of received file:
   - SHA256:10a5b73a30c25a2ff16a5f92665e7174bc28a1c644e955d5cb06653906318258
   - SHA1:7a6efe0980224e7a75a9e34f4f96ae045a8c20e6 [weak]
   - MD5Sum:c6023b3491565cd8e2271916e1bd24c1 [weak]
   - Filesize:516200 [weak]
  Last modification reported: Thu, 26 Apr 2018 23:38:40 +0000
  Release file created at: Thu, 26 Apr 2018 23:37:48 +0000
Get:9 file:/mnt/UBUNTU-REPO/REPO bionic amd64 Contents (deb) [39.5 MB]
Get:19 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main amd64 Packages [266 kB]
Ign:19 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main amd64 Packages
Get:20 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main Translation-en [101 kB]
Ign:20 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main Translation-en
Get:21 file:/mnt/UBUNTU-REPO/REPO bionic-updates amd64 Contents (deb) [5,665 kB]
Ign:21 file:/mnt/UBUNTU-REPO/REPO bionic-updates amd64 Contents (deb)
Get:22 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main amd64 DEP-11 Metadata [138 kB]
Ign:22 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main amd64 DEP-11 Metadata
Get:23 file:/mnt/UBUNTU-REPO/REPO bionic-updates/universe amd64 Packages [138 kB]
Ign:23 file:/mnt/UBUNTU-REPO/REPO bionic-updates/universe amd64 Packages
Get:24 file:/mnt/UBUNTU-REPO/REPO bionic-updates/universe Translation-en [62.4 kB]
Ign:24 file:/mnt/UBUNTU-REPO/REPO bionic-updates/universe Translation-en
Get:25 file:/mnt/UBUNTU-REPO/REPO bionic-updates/universe amd64 DEP-11 Metadata [145 kB]
Ign:25 file:/mnt/UBUNTU-REPO/REPO bionic-updates/universe amd64 DEP-11 Metadata
Get:26 file:/mnt/UBUNTU-REPO/REPO bionic-updates/multiverse amd64 Packages [3,772 B]
Ign:26 file:/mnt/UBUNTU-REPO/REPO bionic-updates/multiverse amd64 Packages
Get:27 file:/mnt/UBUNTU-REPO/REPO bionic-updates/multiverse Translation-en [2,376 B]
Ign:27 file:/mnt/UBUNTU-REPO/REPO bionic-updates/multiverse Translation-en
Get:28 file:/mnt/UBUNTU-REPO/REPO bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Ign:28 file:/mnt/UBUNTU-REPO/REPO bionic-updates/multiverse amd64 DEP-11 Metadata
Get:29 file:/mnt/UBUNTU-REPO/REPO bionic-backports amd64 Contents (deb) [3,555 B]
Ign:29 file:/mnt/UBUNTU-REPO/REPO bionic-backports amd64 Contents (deb)
Get:30 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe amd64 Packages [2,704 B]
Ign:30 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe amd64 Packages
Get:31 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe Translation-en [1,136 B]
Ign:31 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe Translation-en
Get:32 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Ign:32 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe amd64 DEP-11 Metadata
Get:33 file:/mnt/UBUNTU-REPO/REPO bionic-security/main amd64 Packages [125 kB]
Ign:33 file:/mnt/UBUNTU-REPO/REPO bionic-security/main amd64 Packages
Get:34 file:/mnt/UBUNTU-REPO/REPO bionic-security/main Translation-en [49.4 kB]
Ign:34 file:/mnt/UBUNTU-REPO/REPO bionic-security/main Translation-en
Get:35 file:/mnt/UBUNTU-REPO/REPO bionic-security amd64 Contents (deb) [4,564 kB]
Ign:35 file:/mnt/UBUNTU-REPO/REPO bionic-security amd64 Contents (deb)
Get:36 file:/mnt/UBUNTU-REPO/REPO bionic-security/main amd64 DEP-11 Metadata [204 B]
Ign:36 file:/mnt/UBUNTU-REPO/REPO bionic-security/main amd64 DEP-11 Metadata
Get:37 file:/mnt/UBUNTU-REPO/REPO bionic-security/universe amd64 Packages [38.7 kB]
Ign:37 file:/mnt/UBUNTU-REPO/REPO bionic-security/universe amd64 Packages
Get:38 file:/mnt/UBUNTU-REPO/REPO bionic-security/universe Translation-en [22.8 kB]
Ign:38 file:/mnt/UBUNTU-REPO/REPO bionic-security/universe Translation-en
Get:39 file:/mnt/UBUNTU-REPO/REPO bionic-security/universe amd64 DEP-11 Metadata [2,448 B]
Ign:39 file:/mnt/UBUNTU-REPO/REPO bionic-security/universe amd64 DEP-11 Metadata
Get:40 file:/mnt/UBUNTU-REPO/REPO bionic-security/multiverse amd64 Packages [1,440 B]
Ign:40 file:/mnt/UBUNTU-REPO/REPO bionic-security/multiverse amd64 Packages
Get:41 file:/mnt/UBUNTU-REPO/REPO bionic-security/multiverse Translation-en [996 B]
Ign:41 file:/mnt/UBUNTU-REPO/REPO bionic-security/multiverse Translation-en
Get:19 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main amd64 Packages [266 kB]
Get:20 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main Translation-en [101 kB]
Err:20 file:/mnt/UBUNTU-REPO/REPO bionic-updates/main Translation-en
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:818038 [weak]
   - SHA256:f9f43d1a1bf91df6a750ab46cae580c1c4b6dd79e5c796d8f9e6359f760021eb
   - SHA1:37d84249d8fb0ff52817de23c303755cc83a58c6 [weak]
   - MD5Sum:ebaac1badbd5240c89038b03dfed2256 [weak]
  Hashes of received file:
   - SHA256:5a0c019a2beb00b4c95210ed06789776b368b36ef9a4515e386b593fd56009de
   - SHA1:b616bbf992c92edd258c566edadc7565d4b6ef35 [weak]
   - MD5Sum:f12bcce91fecde25ebf621e8f0071464 [weak]
   - Filesize:101120 [weak]
  Last modification reported: Wed, 25 Jul 2018 23:45:07 +0000
  Release file created at: Thu, 26 Jul 2018 01:48:42 +0000
Get:21 file:/mnt/UBUNTU-REPO/REPO bionic-updates amd64 Contents (deb) [5,665 kB]
Get:29 file:/mnt/UBUNTU-REPO/REPO bionic-backports amd64 Contents (deb) [3,555 B]
Get:30 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe amd64 Packages [2,704 B]
Get:31 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe Translation-en [1,136 B]
Get:32 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:33 file:/mnt/UBUNTU-REPO/REPO bionic-security/main amd64 Packages [125 kB]
Get:34 file:/mnt/UBUNTU-REPO/REPO bionic-security/main Translation-en [49.4 kB]
Err:31 file:/mnt/UBUNTU-REPO/REPO bionic-backports/universe Translation-en
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:2668 [weak]
   - SHA256:d75725acc41c3438e40db9700a5be9ebe3f57a5ed4744b14226c9306b631a2d8
   - SHA1:d2a6be8a857312705e3edba513efec15ce60242b [weak]
   - MD5Sum:602ad4427a31d34322ccf1ad5827b04b [weak]
  Hashes of received file:
   - SHA256:a9357002259cb7e20398b4d5463e57661bada70d416dc9a71b56003624b4c6fb
   - SHA1:bf194ab9003314a4ea559da35c1c7a0be2f762ef [weak]
   - MD5Sum:067478e6ce3a3669ca9836d2ae55a4fa [weak]
   - Filesize:1040 [weak]
  Last modification reported: Wed, 25 Jul 2018 23:45:21 +0000
  Release file created at: Thu, 26 Jul 2018 01:49:00 +0000
Err:34 file:/mnt/UBUNTU-REPO/REPO bionic-security/main Translation-en
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:435883 [weak]
   - SHA256:2f72f79acfb50d14fe1d621f1fa891352d15aafc309f755e34582d2917012719
   - SHA1:a7f4baab23f2ea7e6f33d78c3ea8fa461a8d4cfe [weak]
   - MD5Sum:64630fcf40e76a8c1f85f5cd1abd2fb0 [weak]
  Hashes of received file:
   - SHA256:86a2ef7099e2c3c9cb221c589cd8e3b3b96cc7646d4adebdf2e20e1fe5006825
   - SHA1:01a46d7c71c2e87b75e2a8885da013b81774952b [weak]
   - MD5Sum:e8704e9fd3624f865099bf0c5c85c5be [weak]
   - Filesize:49392 [weak]
  Last modification reported: Wed, 25 Jul 2018 23:44:59 +0000
  Release file created at: Thu, 26 Jul 2018 01:48:36 +0000
Get:35 file:/mnt/UBUNTU-REPO/REPO bionic-security amd64 Contents (deb) [4,564 kB]
Reading package lists... Done
E: The repository 'file:/mnt/UBUNTU-REPO/REPO/GNS3/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

So I installed apache and made the repository accessible via http and changed the /etc/apt/sources.list
```

deb [arch=amd64] http://localhost/repo bionic main restricted universe multiverse
deb [arch=amd64] http://localhost/repo bionic-updates main restricted universe multiverse
deb [arch=amd64] http://localhost/repo bionic-backports main restricted universe multiverse
deb [arch=amd64] http://localhost/repo bionic-security main restricted universe multiverse
deb [arch=amd64] http://localhost/gns3/ppa/ubuntu bionic main
```

Things seem to be working fine now!!

I also tested by changing my /etc/apt/sources.list file to use online repository
```

deb [arch=amd64] http://ftp.iinet.net.au/pub/ubuntu bionic main restricted universe multiverse
deb [arch=amd64] http://ftp.iinet.net.au/pub/ubuntu bionic-updates main restricted universe multiverse
deb [arch=amd64] http://ftp.iinet.net.au/pub/ubuntu bionic-backports main restricted universe multiverse
deb [arch=amd64] http://ftp.iinet.net.au/pub/ubuntu bionic-security main restricted universe multiverse
deb [arch=amd64] http://ppa.launchpad.net/gns3/ppa/ubuntu bionic main
```
 
and things worked just fine.

So, in conclusion all I can guess is that when the "file;/" protocl is used in /etc/apt/sources.list Hash Sum Mismatch occurs??

Any light on the issue will be greatly appreciated..
Thanks in advance
Emon

---

