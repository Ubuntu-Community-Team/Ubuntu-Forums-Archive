---
title: "Can't get updates from apt-get, aptitude or synaptic"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by vdubber on 2007-05-10
Hi, I can't get any updates, can anyone help? Using Dapper apt-get update has worked once in a week of trying. I've tried several different sources.list files with no effect. All I see is the following
```

jez@jez-ubuntu:~$ sudo apt-get update
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://medibuntu.sos-sts.com dapper Release.gpg
  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Errhttp://it.archive.ubuntu.com dapper Release.gpg
  Could not connect to it.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to it.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed outFailed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg  Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Below is my current sources.list file that gave the above error.

```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```
Is it a problem with my router?

Cheers

---

### Post by Vikstar on 2008-05-07
Open the Synaptic Package Manager, go to "Settings", "Repositories", "Ubuntu Software", then change "Download From:" to "Main server" or add another server.

---

