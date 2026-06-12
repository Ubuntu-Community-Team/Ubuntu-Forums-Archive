---
title: "Becoming less than thrilled with 10.04 ..."
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2010-07-23
After a rash of updates I'm becoming less than thrilled with 10.04.  Quite a disappointment since the initial installation experience was so good (although I had resolved all the grub2 frustrations with 9.10 and 10.04beta -- I still fail to see the point of grub2, however).  

The "Plymouth" boot splash stuff has never worked for me, IMHO a total waste of development resources, but the system does boot faster than all its predecessors and even Windows 7. But it is annoying to be blind during system startup, although since I reboot so infrequently its not an issue, until I encounter a boot up problem :(.

VirtualBox stopped working, the DKMS thing failed to automatically rebuild the Virtualbox modules so I had to do it manually.

Bunch of autoremovable packages were left behind, followed by some hopefully unimportant error messages during apt-get autoremove:

```
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

```

And the biggest irritation is CD/DVD burning is broke -- I have to dual boot into 8.04 to burn disks, so I know its not a hardware issue :(

---

