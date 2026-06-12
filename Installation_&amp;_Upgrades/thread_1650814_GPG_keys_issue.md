---
title: "GPG keys issue"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by mhdbnoimi on 2010-12-22
Hi All,

When I tried to upgrade (update) current packages list in my synaptic I got error messages about unresolved gpg keys as following:

```
W: GPG error: http://qt-kde.debian.net experimental-snapshots Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 93DD2AE2E79C8BAB
W: GPG error: http://linux-mint.froonix.org julia Release: The following signatures were invalid: BADSIG 3EE67F3D0FF405B2 Clement Lefebvre (Linux Mint Package Repository v1) <root@linuxmint.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.getdeb.net maverick-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>

W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://progprak.scale.uni-koeln.de/lazarus/dists/lazarus-testing/universe/source/Sources.gz  404  Not Found

W: Failed to fetch http://progprak.scale.uni-koeln.de/lazarus/dists/lazarus-testing/universe/binary-amd64/Packages.gz  404  Not Found

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

How I can get all missed keys for completing update process?

---

### Post by karthick87 on 2010-12-22
Type the following in terminal,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E79C8BAB
```
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 46D7E7CF
```
```
sudo apt-get update
```

---

### Post by mhdbnoimi on 2010-12-22
> **karthick87 said:**
> Type the following in terminal,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E79C8BAB
```


It didn't work! here is the log:
```
mbnoimi@mbnoimi-pc ~ $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E79C8BAB
[sudo] password for mbnoimi: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys E79C8BAB
gpg: requesting key E79C8BAB from hkp server keyserver.ubuntu.com
gpgkeys: key E79C8BAB not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

> **karthick87 said:**
> Type the following in terminal,
```
sudo apt-get update
```
I'm still have some issues...another help please, by karthick87 solution i fixed one issue
```
W: GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://qt-kde.debian.net experimental-snapshots Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 93DD2AE2E79C8BAB
W: GPG error: http://linux-mint.froonix.org julia Release: The following signatures were invalid: BADSIG 3EE67F3D0FF405B2 Clement Lefebvre (Linux Mint Package Repository v1) <root@linuxmint.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.getdeb.net maverick-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by oldos2er on 2010-12-22
If you visit the link shown, [http://qt-kde.debian.net](http://qt-kde.debian.net), there should be info on getting the key.

---

### Post by mhdbnoimi on 2010-12-25
> **oldos2er said:**
> If you visit the link shown, [http://qt-kde.debian.net](http://qt-kde.debian.net), there should be info on getting the key.

hmmm, sure I visited that page but as mentioned there:
> In order to get repository key, install the pkg-kde-archive-keyring package:
```
aptitude install pkg-kde-archive-keyring
```


I couldn't find **pkg-kde-archive-keyring** package!

---

### Post by karthick87 on 2010-12-25
Post the results of sources.list
```
cat /etc/apt/sources.list
```

---

### Post by oldos2er on 2010-12-25
> **mhdbnoimi said:**
> hmmm, sure I visited that page but as mentioned there:


I couldn't find **pkg-kde-archive-keyring** package!

[http://qt-kde.debian.net/debian/pool/main/p/pkg-kde-archive-keyring/pkg-kde-archive-keyring_2.1_all.deb](http://qt-kde.debian.net/debian/pool/main/p/pkg-kde-archive-keyring/pkg-kde-archive-keyring_2.1_all.deb)

---

### Post by mhdbnoimi on 2010-12-26
> **karthick87 said:**
> Post the results of sources.list
```
cat /etc/apt/sources.list
```

```
mbnoimi@admino-mbnoimi ~ $ cat /etc/apt/sources.list
deb http://packages.linuxmint.com/ julia main upstream import romeo backport
deb http://archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ maverick partner
deb http://packages.medibuntu.org/ maverick free non-free
deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
deb http://archive.getdeb.net/ubuntu maverick-getdeb games
deb http://qt-kde.debian.net/debian experimental-snapshots main
deb-src http://qt-kde.debian.net/debian experimental-snapshots main

mbnoimi@admino-mbnoimi ~ $ ls /etc/apt/sources.list.d/                                                                                                                                         
local-repository.list  local-repository.list.save
```

---

