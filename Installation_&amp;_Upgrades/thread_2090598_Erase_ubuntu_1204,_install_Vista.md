---
title: "Erase ubuntu 12/04, install Vista"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by kvalenza on 2012-12-02
Yes, I know Vista is not a good OS and the Ubuntu is better. However, I am trying to sell a good used computer that has Ubuntu on it, and I want to replace it with Vista. I am not able to do it because there is apparently no NFTS on it. I have done a search on Google, and none of the answers I have seen make any sense to me. I just want to eliminate Ubuntu and replace it with Vista on one computer. Is there a simple way I can do this? All that is available is a logical drive and a primary drive. I am not able to format anything with the Vista disk, and it won't let me install anything. If anyone really knows how to do this, please let me know...as simply as possible, one step at a time. Thanks.

---

### Post by Hylas de Niall on 2012-12-03
Reboot from a live CD (Linux), open Gparted, reformat the two partitions to ntfs.
Boot again from Vista and it should see the drives as usable, and install.

HTH

---

### Post by 2F4U on 2012-12-03
If this is a dual boot configuration, removing Ubuntu may be not enough, since this won't remove Grub. You can use the Vista installation CD to restore the Windows MBR:

[http://quainttech.blogspot.de/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.de/2007/05/how-to-remove-ubuntu-from-vista-dual.html)
[http://www.ehow.com/how_4900104_uninstall-ubuntu-install-windows.html](http://www.ehow.com/how_4900104_uninstall-ubuntu-install-windows.html)

---

