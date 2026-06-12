---
title: "installing amd64 dapper via netboot can't find grub"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by jgilbertsjc on 2006-06-22
I've got two somewhat old (but new to me) machines I'm trying to get Dapper installed onto. These are: 
  - Dual AMD64 2.0G, 8GB RAM, 1 ICP Vortex SCSI with 6 70G SCSI drives on one channel, configured for 1 R5 volume (during install, this drive is partitioned into one 1GB part for /, 4GB for swap, and the rest is left to LVM2).

I've got the nodes successfully loading and installing Dapper 6.06 server over the network, and through an approx Ubuntu proxy (the approx configs are below [1]).  Everything goes well, up to the point of getting a boot loader.

For either grub -or- lilo, the install process fails and says that it was unable to install grub. Looking at the logs on the approx server shows the following: 

```
Jun 22 12:37:43 localhost approx: Connection from 10.0.1.1
Jun 22 12:37:43 localhost approx: Request /ubuntu/pool/main/g/grub/grub_0.97_1ubuntu9_amd64.deb
Jun 22 12:37:43 localhost approx:   connection: Keep-Alive
Jun 22 12:37:43 localhost approx:   host: 10.0.1.20:9999
Jun 22 12:37:43 localhost approx:   accept: */*
Jun 22 12:37:43 localhost approx:   user-agent: Wget/1.10.2 (Red Hat modified)
Jun 22 12:37:43 localhost approx: http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97_1ubuntu9_amd64.deb
Jun 22 12:37:44 localhost approx:   HTTP/1.1 404 Not Found
Jun 22 12:37:44 localhost approx:   Date: Thu, 22 Jun 2006 19:37:44 GMT
Jun 22 12:37:44 localhost approx:   Server: Apache/2.0.55 (Ubuntu)
Jun 22 12:37:44 localhost approx:   Vary: accept-language,accept-charset
Jun 22 12:37:44 localhost approx:   Accept-Ranges: bytes
Jun 22 12:37:44 localhost approx:   Transfer-Encoding: chunked
Jun 22 12:37:44 localhost approx:   Content-Type: text/html; charset=iso-8859-1
Jun 22 12:37:44 localhost approx:   Content-Language: en
Jun 22 12:37:44 localhost approx: HTTP proxy response: 404
Jun 22 12:37:44 localhost approx:   Date: Thu, 22 Jun 2006 19:37:44 GMT
Jun 22 12:37:44 localhost approx:   Server: Apache/2.0.55 (Ubuntu)
Jun 22 12:37:44 localhost approx:   Content-Type: text/html; charset=iso-8859-1

```

...which results in a failure on the install clients. Running 'apt-install grub' manually outside of the install walkthrough produces a '400 Bad Request' message in the client's /var/log/syslog [3]. Running the downloaded 'grub-installer' on the client produces similar results; it seems like it's asking for a file that exists in the Packages just doesn't exist on the archives. 

The Packages.gz's were just pulled down and seem to be ok; their md5sum are below[2]. Taking the approx caching mirror out of the picture doesn't work, either; the install fails in exactly the same way against the us.archive.ubuntu.com mirrors. 

Both grub and lilo fail in the same way.

This is not an FAI or hands-off install; we're hitting 'server' at the boot prompt ('server expert' produces the same result), and then walking through the install itself. 

I don't have alternate hardware to try to replicate this, so I'm unsure if it's related to the underlying hardware (which I can't imagine that it is, but certianly open to that suggestion) or an incompatability or what.

Attempting to download grub manually to the install client works *but* fails dpkg installation with a number of 'udeb' dependancies, so I can only imagine that this is certianly not something I should be doing. 

Has anyone seen this before? What's happening with apt, and how can this be fixed?

TIA, 

j.

[1] approx config: 
```
port            9999
interval        1720
debug           true
ubuntu          http://us.archive.ubuntu.com/ubuntu
dapper          http://us.archive.ubuntu.com/ubuntu
universe        http://us.archive.ubuntu.com/ubuntu
security        http://security.ubuntu.com/ubuntu
breezy          http://us.archive.ubuntu.com/breezy

```

[2]:
```
1843fceff6efd0cacbcfe205ebe5853d  ubuntu/dists/dapper-security/main/binary-amd64/Packages.bz2
50a41b9ab9bedc6036356fdae819331f  ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.bz2
5efaac9f6b8566f656956b05ee19f9a1  ubuntu/dists/dapper/main/binary-amd64/Packages.gz
b4766612b185ab8d62dfa392fd3c1aa3  ubuntu/dists/dapper/main/debian-installer/binary-amd64/Packages.gz
f1531be6d0f50ce3b511941af8b78f6d  ubuntu/dists/dapper/restricted/binary-amd64/Packages.bz2
f75e18781e844276be88f94fe2ae46ea  ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz
21461683f8d867cb199c7facf9c61e2b  ubuntu/dists/dapper/restricted/debian-installer/binary-amd64/Packages.gz
9f837c054b908b9181ed3720ff3559d2  ubuntu/dists/dapper-updates/main/binary-amd64/Packages.bz2
bc874c0dd761f6ad5c40b65842da821d  ubuntu/dists/dapper-updates/main/debian-installer/binary-amd64/Packages.gz
4059d198768f9f8dc9372dc1c54bc3c3  ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.bz2
4a4dd3598707603b3f76a2378a4504aa  ubuntu/dists/dapper-updates/restricted/debian-installer/binary-amd64/Packages.gz

```

[3]: Error log from the install client's /var/log/syslog. Note: transcribed by hand.
```

apt-install: Reading package lists...
apt-install: Building dependancy tree....
apt-install: 
apt-install: Suggested packages: 
apt-install:   grub-doc grubconf
apt-install: The following NEW packages will be installed:
apt-install:   grub
apt-install: 0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded
apt-install: Need to get 836kB of archives
apt-install: After unpacking 1733kB of additional disk space will be used.
apt-install: Err http://10.0.1.20 dapper/main grub 0.97-1ubuntu9
apt-install:   400 Bad request
apt-install: Failed to fetch http://10.0.1.20:9999/ubuntu/pool/main/g/grub/grub_0.97-1ubuntu9_amd64.deb  400 Bad request
apt-install: E:
apt-install: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
grub-installer: info: Calling 'apt-install grub' failed

```

---

### Post by jgilbertsjc on 2006-06-26
As a follow-up to this, we turned down approx and loaded up apt-proxy-v2 to test, and sure enough, it worked. *bobble*

No idea why approx couldn't find the grub package, or why it couldn't (or didn't) load it directly from the outside network.  *shrug*

---

