---
title: "apt-cdrom add fails"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by pksings on 2005-10-14
The following are the results of apt-cdrom add and apt-key list
Any help in fixing this will be and is much appreciated..


Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
This disc is called:
'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
Copying package lists...gpgv: Signature made Wed Oct 12 09:25:36 2005 PDT using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/breezy/Release.gpg


root@dell-pk:~ # apt-key list
/etc/apt/trusted.gpg
--------------------
pub  1024D/437D05B5 2004-09-12 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub  2048g/79164387 2004-09-12

---

