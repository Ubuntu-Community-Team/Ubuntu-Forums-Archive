---
title: "Feisty Upgrade - Problem with mounted share"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by alandean on 2007-05-09
We have a number of machines which I recently upgraded to Feisty.  These used to all mount  a shared folder on a 'server' running 'Breezy Badger' which we do not intend upgrading.

Immediately after the upgrade the machines were tested and could mount the network share correctly which is confgured in 'fstab' as follows:

//BreezyServer/SharedFolder		/MountFolder		smbfs	fmask=777,dmask=777	0	0

While testing this worked fine, but now we have a problem.  The 'MountFolder' does not appear as a folder in the 'Filesystem', and when using 'ls -l' the folder appears as follows:

'?---------   ? ?    ?        ?                    ?  MountFolder'

Trying to 'umount -a' and 'mount -a' produces the message:

'Could not resolve the mount point /MountFolder'

I can't seem to find this problem highlighted anywhere, and I'm getting a bit of grief from our users asking why I felt the need to upgrade when their machine was working fine!!!!!

Please help.

---

