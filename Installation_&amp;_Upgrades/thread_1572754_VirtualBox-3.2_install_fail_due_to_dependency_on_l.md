---
title: "VirtualBox-3.2 install fail due to dependency on libssl0.9.8-m"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by Henry P on 2010-09-11
Hello

When following the VirtualBox installation process([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)) 
  The installation aborts due to missing libssl0.9.8

Any idea of what I'm missing here, what might I might be missing in my process?
  Thanks 

   Henrik

I get:

```
apt-get install virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-3.2: Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8 is to be installed
E: Broken packages
```Linux box 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
/etc/debian_version  => squeeze/sid

```

apt-cache show libssl0.9.8
Package: libssl0.9.8
Priority: required
Section: libs
Installed-Size: 2332
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Source: openssl
Version: 0.9.8k-7ubuntu8
Depends: libc6 (>= 2.7), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0
Conflicts: libssl, libssl096-dev (<< 0.9.6-2), openssl (<< 0.9.6-2), ssleay (<< 0.9.2b)
Filename: pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8_amd64.deb
Size: 976464
MD5sum: 46c45046414d5134d5df66742eaa0935
SHA1: c8edeae1495d34a8eacceebf51893de903f7cff2
SHA256: d2df118898d9fd979e49c9091bf67a193dd722bf8b9e05d6c0bf18f3524c311b
Description: SSL shared libraries
 libssl and libcrypto shared libraries needed by programs like
 apache-ssl, telnet-ssl and openssh.
 .
 It is part of the OpenSSL implementation of SSL.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: minimal

``````
apt-get install libssl0.9.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl0.9.8 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

