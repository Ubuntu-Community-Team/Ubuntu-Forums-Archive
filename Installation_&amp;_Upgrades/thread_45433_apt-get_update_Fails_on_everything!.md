---
title: "apt-get update Fails on everything!"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by RossC0 on 2005-06-30
Hi,

When I do apt get update it fails on every url!

i.e.
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz)  302 Found

When I surf to archive.ubuntu.com I get  'Real Time Enterprises' web site ?? 

Any ideas why it won't update ??

---

### Post by RossC0 on 2005-06-30
OK - most of the repositiories seem to be back up!

Now I cant re-add my ubuntu cd - 

when i do apt-cdrom add I get:

Identifying.. [7340c3e4349fe3792b92f8f71cfe7ab3-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
Copying package lists...gpgv: Signature made Thu 07 Apr 2005 04:30:36 BST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/hoary/Release.gpg


Any ideas ??

---

