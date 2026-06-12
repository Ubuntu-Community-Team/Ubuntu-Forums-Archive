---
title: "Lots of NO_PUBKEY GPG errors when trying to update."
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2015-12-12
Hi,

I am suddenly getting lots of GPG NO_PUBKEY error messages when trying to do a 'sudo apt-get update'. I have not changed or done anything that should be causing this. The errors are:

```
W: GPG error: [http://apt.insynchq.com](http://apt.insynchq.com) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06BBDC2602DFE7E7
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) wily-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://repo.vivaldi.com](http://repo.vivaldi.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CEC384A8BF1700F8
```

I have tried to add the keys with 'sudo gpg --keyserver keyserver.ubuntu.com --recv-keys XXXXXXXXXX' but it doesn't fix the problem. The same errors are back again next time I do an update. This is the typical output I get when trying to add them:

```
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

What can I do to fix this problem? Since I haven't made any changes to my computer myself I have no idea how or why this happened.

---

### Post by v3.xx on 2015-12-14
I would try this.

[http://ubuntuforums.org/showthread.php?t=1869890&page=2&p=11396851#post11396851](http://ubuntuforums.org/showthread.php?t=1869890&page=2&p=11396851#post11396851)

---

