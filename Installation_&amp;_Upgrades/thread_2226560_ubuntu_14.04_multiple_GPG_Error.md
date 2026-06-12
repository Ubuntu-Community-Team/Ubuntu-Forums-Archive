---
title: "ubuntu 14.04 multiple GPG Error"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by hgabe on 2014-05-27
```
W: GPG error: [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9ECBEC467F0CEB10
W: GPG error: [http://mirrors.advancedhosters.com](http://mirrors.advancedhosters.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://mirrors.advancedhosters.com](http://mirrors.advancedhosters.com) trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://mirrors.advancedhosters.com](http://mirrors.advancedhosters.com) trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://download.bitdefender.com](http://download.bitdefender.com) bitdefender Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A373FB480EC4FE05
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: [http://liveusb.info](http://liveusb.info) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4E940D7FDD7FB8CC
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://developer.download.nvidia.com](http://developer.download.nvidia.com)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D88C3D385C37D3BE
W: GPG error: [http://ftp.yz.yamagata-u.ac.jp](http://ftp.yz.yamagata-u.ac.jp) saucy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBCB082A1BB943DB
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 620396F19C0042C8
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0C14D55CE7242835
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
```


I tried this already but it didn't have any effect


>              Try deleting the key

  sudo apt-key del 16126D3A3E5C1192
  then updating the repository
  sudo apt-get update
  You should get a NO_PUBKEY error instead of a BADSIG error and
  sudo apt-key finger
  should **not** find the key (called "Ubuntu Extras Archive Automatic Signing Key")
  Now add the key
  sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
  The result of apt-key finger should have
  pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
  [HR][/HR]  If that does not work, try
  apt-get clean            # Remove cached packages
cd /var/lib/apt
mv lists lists.old       # Backup mirror info
mkdir -p lists/partial   # Recreate directory structure
apt-get clean
apt-get update           # Fetch mirror info
  Source: [this]("http://ubuntuforums.org/showthread.php?p=10961816") ubuntu forums thread
      



```

gpg: keyblock resource `/etc/apt/trusted.gpg.d/vascofalves-gnome-backports.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-atom.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-gthumb.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-java.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-nemo.gpg': resource limit
gpg: keyblock resource `/etc/apt/trusted.gpg.d/webupd8team-tor-browser.gpg': resource limit
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: key 4C9D234C: "Launchpad webupd8" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```


I get unchanged when I try adding all those keys

---

### Post by oldos2er on 2014-06-01
Could be this bug: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)

Read post #1 in the above link for a possible solution.

---

