---
title: "upgrade from 10.04 to 12.04 without internet but with local mirror repo"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by Diamond2 on 2013-01-22
I created the local mirror to upgrade all lucid workstations in my network to precise. The problem is that the upgrade tool (link below) - precise.tar.gz always download packages from archive.ubuntu.com (19% [Waiting for headers] [Connecting to archive.ubuntu.com (91.189.92.153)]). I edited the precise.tar.gz file by modifying some files of it, putting it to my local mirror, modified the meta-release URL to my local mirror. Running do-release-upgrade I have the error below. My question is how to sign the precise.tar.gz package myself?


```


    Checking for a new ubuntu release

    Done Upgrade tool signature

    Done Upgrade tool

    Done downloading

    authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg'

    exception from gpg: GnuPG exited non-zero, with code 1

    Debug information:

    gpg: Signature made Mon 04 Jun 2012 08:40:31 PM ICT using DSA key ID 437D05B5

    gpg: /tmp/tmpMaz62f/trustdb.gpg: trustdb created

    gpg: BAD signature from "Ubuntu Archive Automatic Signing Key "

    Authentication failed

    Authenticating the upgrade failed. There may be a problem with the network or with the server.

```


```
Dist: precise
Name: Precise Pangolin
Version: 12.04 LTS
Date: Thu, 26 Apr 2012 12:04:00 UTC
Supported: 1
Description: This is the 12.04 LTS release
Release-File: http://archive.ubuntu.com/ubuntu/dists/precise/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/precise-security/main/dist-upgrader-all/current/ReleaseAnnouncement
ReleaseNotesHtml: http://archive.ubuntu.com/ubuntu/dists/precise-security/main/dist-upgrader-all/current/ReleaseAnnouncement.html
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/precise-security/main/dist-upgrader-all/current/precise.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/precise-security/main/dist-upgrader-all/current/precise.tar.gz.gpg
```

---

### Post by dino99 on 2013-01-22
[http://askubuntu.com/questions/127923/how-can-i-update-ubuntu-offline-without-using-synaptic-or-keryx](http://askubuntu.com/questions/127923/how-can-i-update-ubuntu-offline-without-using-synaptic-or-keryx)

---

