---
title: "Can I install an older version of Ubuntu over the previous in the same partition?"
date: 2019-06-22
forum: Installation &amp; Upgrades
---

### Post by shubanshii on 2019-06-22
I'm dual booting Windows 10 and Ubuntu 19.04 and want to downgrade Ubuntu to 18.04. I'm fine losing my files.

Can I install the 18.04 over the 19.04?  Do I have to reformat the Ubuntu partition, change Windows to primary boot and start over?

---

### Post by Dennis N on 2019-06-22
Yes, you can install 18.04 over 19.04 by using the 'something else' option at the bottom of the 'installation type' screen. On the next screen (shows partitions), select the current 19.04 partition, then click on the 'change' button. In the popup window, specify how to use this partition in the new install:

use as ext4 journalled file system
mount at /
you should select the format (as ext4) option

The boot loader location at the bottom only works with bios installs; if doing uefi (you probably are) then you can ignore it.
Now ready to click install, supply your user information and finish.

---

### Post by shubanshii on 2019-06-23
Thank you very much Dennis.  That procedure went very smoothly.

---

