---
title: "Hardy, update manager: current dist not found in meta-release file"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by hermes0710 on 2008-04-25
I get this message in the console when running the update-manager

```
current dist not found in meta-release file

```

My  /var/lib/update-manager/meta-release-lts 
```

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 1
Description: This is the Dapper Drake release
Release-File: http://archive.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/DapperReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/dapper /main/dist-upgrader-all/current/dapper.tar.gz.gpg
```

I get not updates (i don't know if they exist though)

---

### Post by fishtoprecords on 2008-04-27
I have this as well. Hardy Heron is not in the file.
also not in meta-release as well.

---

### Post by hermes0710 on 2008-04-29
Do you believe that when updates are available, the update manager will know that?

---

### Post by fishtoprecords on 2008-05-07
I know that I didn't change anything, and later, when updates to Hardy were available, the standard update manager found them and installed them. So the message seems mostly harmless.

---

