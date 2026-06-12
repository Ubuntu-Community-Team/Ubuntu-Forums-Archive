---
title: "Upgrade to 17.10 fails dues to Hash Sum mismatch"
date: 2017-10-21
forum: Installation &amp; Upgrades
---

### Post by jdogzilla2 on 2017-10-21
I am unable to upgrade from Kubuntu 17.04 to 17.10 (both 64bit).  I always get stuck with this message below.  I have tried changing the server to US servers and Main servers, deleted all files in /var/cache/apt/lists/* and apt-get clean, but always end up with the same message below.  Any advice would be great. 


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-i386/by-hash/SHA256/fe3a663163e1069bc115d25e47e4f1cd1badab6e638f730e3cae8138fe73a048](http://us.archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-i386/by-hash/SHA256/fe3a663163e1069bc115d25e47e4f1cd1badab6e638f730e3cae8138fe73a048)  Hash Sum mismatch
Hashes of expected file:
 - Filesize:222932 [weak]
 - SHA256:fe3a663163e1069bc115d25e47e4f1cd1badab6e638f730e3cae8138fe73a048
 - SHA1:6f1146b30bd80189d4401cb16f76cf2dbcfda3f7 [weak]
 - MD5Sum:107b6140b9bf7bd51a46d356fb77caca [weak]
Hashes of received file:
 - SHA256:a56c328a3441f723f6fb7e0242cc94b2758685885c963afe3b2f2c4718a3c3a5
 - SHA1:a548bc5ada56d86112650419d9c88698d785b436 [weak]
 - MD5Sum:1675775ca9488ae560348d88fada2845 [weak]
 - Filesize:222932 [weak]
Last modification reported: Sat, 21 Oct 2017 00:33:53 +0000
Release file created at: Sat, 21 Oct 2017 01:23:35 +0000
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-amd64/by-hash/SHA256/a0b599191a206993e417b6065939be970d2a3475a56b8e2ba08d7eeb178aa1ee](http://us.archive.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-amd64/by-hash/SHA256/a0b599191a206993e417b6065939be970d2a3475a56b8e2ba08d7eeb178aa1ee)  Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jdogzilla2 on 2017-10-21
After doing ... 
sudo rm -rf /var/lib/apt/lists/partial
sudo apt-get update -o Acquire::CompressionTypes::Order::=gz

This is what I get at the second step of the upgrade ... 
E:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/artful/multiverse/binary-i386/by-hash/SHA256/d1f9e7ec6489f3540ddd3399c345799e46d2e1213570f510ca41bd12d5b9407e](http://us.archive.ubuntu.com/ubuntu/dists/artful/multiverse/binary-i386/by-hash/SHA256/d1f9e7ec6489f3540ddd3399c345799e46d2e1213570f510ca41bd12d5b9407e)  Hash Sum mismatch
Hashes of expected file:
 - Filesize:142776 [weak]
 - SHA256:d1f9e7ec6489f3540ddd3399c345799e46d2e1213570f510ca41bd12d5b9407e
 - SHA1:16f5314466b815e49a6b53124ba88bd434304b9e [weak]
 - MD5Sum:c7b94987695731eb16b07c5bb0c8311d [weak]
Hashes of received file:
 - SHA256:8da861b95323d6b98fdcc24324eee84baa90aa6159cf9b7134fe81432639e14e
 - SHA1:9ecda16f6e859d480eacde0b06800c58f7d7a43e [weak]
 - MD5Sum:f8c8486e5ab253cb02209022ff3d0dc1 [weak]
 - Filesize:142776 [weak]
Last modification reported: Wed, 18 Oct 2017 08:50:51 +0000
Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

