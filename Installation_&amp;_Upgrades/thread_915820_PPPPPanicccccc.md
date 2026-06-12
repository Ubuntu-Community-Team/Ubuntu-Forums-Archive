---
title: "PPPPPanicccccc"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-09-10
I have delete Software Sources/Authentication contents by mistake, now
when I run update manager I get the following 


W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Is there a way to correct this ?

---

### Post by Partyboi2 on 2008-09-10
Open a terminal and try
```
sudo apt-key update
```
then
```
sudo apt-get update
```

---

