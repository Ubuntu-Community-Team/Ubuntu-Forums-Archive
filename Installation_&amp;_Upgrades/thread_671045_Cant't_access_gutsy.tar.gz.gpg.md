---
title: "Cant't access gutsy.tar.gz.gpg"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by fst_odl on 2008-01-18
Hi,

I can't access the file [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg). I tried also to access the gpg file in 0.79 and 0.80, and even tried [http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg) - I seem to be unable to read any gpg file. Does anyone have the same problem? 

Cheers, Frank

---

### Post by kevdog on 2008-01-18
I cant even dowload anything from those links you provided.  Are those correct?  .gpg would imply those files are encrypted would need to be decrypted using gpg with the public key of the distributor.

---

### Post by zvacet on 2008-01-18
```
sudo apt-get update
```

---

### Post by fst_odl on 2008-01-21
The links are correct. I noticed this problem because I tried to do an upgrade, that is 

```
root@ubuntu:~# aptitude update
[...]
root@ubuntu:~# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmp6Ek67j/gutsy.tar.gz'
authenticate '/tmp/tmp6Ek67j/gutsy.tar.gz' against '/tmp/tmp6Ek67j/gutsy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:

gpg: WARNING: unsafe permissions on homedir `/tmp/tmp6Ek67j'

gpg: verify signatures failed: eof

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.
```


After that I tried to load the file manually. The address ist part of the file "/var/lib/update-manager/meta-release"

---

### Post by Partyboi2 on 2008-01-21
You could try what is suggested here

[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/156070](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/156070)

---

### Post by fst_odl on 2008-01-22
I cant't download the file manually - I've tried it with wget and with firefox.

---

### Post by Partyboi2 on 2008-01-22
Having a little look through google, some people who had the same error were able to get it fixed by
Opening a terminal
and type
```
gpg
```It will say
> Go ahead and type your message...press 
```
ctrl+c
```then run
```
sudo update-manager -c -d
```

---

### Post by fst_odl on 2008-01-23
I tried that too, but that didn't work. It really seems that the file is unreadable - are you able to download the file?

---

### Post by Partyboi2 on 2008-01-23
No I can't download the file either. The screenshot shows what I get.

---

