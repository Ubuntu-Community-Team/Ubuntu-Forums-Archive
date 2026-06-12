---
title: "ubuntu 9.10 software source error"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by golden_eye_ on 2010-03-06
hello all ...
reloading the software sources in ubuntu 9.10 is generating the following error ??
what can i do ??

> 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.


Thanks in advance

---

### Post by MelDJ on 2010-03-06
try changing you software server in software sources

---

### Post by golden_eye_ on 2010-03-06
Thanks ....
Solved

---

### Post by wcorey on 2010-03-31
I have the same problem and it hasn't gone away after repeated apt-get updates..

Fetched 60.6MB in 2min 29s (405kB/s)                                           
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.1.1-5ubuntu1.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.1.1-5ubuntu1.1_amd64.deb)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.0-3ubuntu5.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.0-3ubuntu5.6_amd64.deb)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.6_amd64.deb)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1_amd64.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
This has gone for days. What do I try now, it is a fresh install of 9.10 Desktop.

Thanks,

Walt

---

