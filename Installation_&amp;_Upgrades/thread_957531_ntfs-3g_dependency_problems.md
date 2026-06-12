---
title: "ntfs-3g: dependency problems"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by chinnusan on 2008-10-24
i.. am santosh from bengaluru..
i have installed dapper drake on windows xp sp2.. and i am unable to write in the ntfs windows from ubuntu dapper drake so i changed lines in the fstab as

/dev/hda2       /media/hda2     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda5       /media/hda5     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/hda6       /media/hda6     ntfs-3g defaults,locale=en_US.utf8 0 0

but it is not working.. before by default it was atleast able to read the ntfs windows partitions but now am unable to open also.. please help me out immediately.. am using pentium celeron 766mhz processor and total 384mb sd ram and 80 gb segate harddisk..
and am getting error for ntfs-3g also as::

E: fuse-utils: subprocess post-installation script returned error exit status 1
E: ntfs-3g: dependency problems - leaving unconfigured
E: ntfs-config: dependency problems - leaving unconfigured

and error for wine:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY

---

