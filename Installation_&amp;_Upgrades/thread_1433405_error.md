---
title: "error"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by MughalShahzad on 2010-03-19
Why following error occurred

                          GPG error: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F719C35E394D996Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 Some index files failed to download, they have been ignored, or old ones used instead.


Thanks & Regards
Shahzad

---

### Post by MelDJ on 2010-03-19
for the pub key error, try the link in my sig.
you seem to have added the cd to your software sources. remove it by going to system-admin-software sources.
under the ubuntu software tab, deselect the cdrom

---

