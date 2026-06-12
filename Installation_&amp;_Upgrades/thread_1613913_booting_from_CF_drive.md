---
title: "booting from CF drive"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by jbuczek on 2010-11-05
I have a micro-atx box with a CF reader that pretends it's an IDE HDD. You can boot off this thing and this is intended to be a "diskless" system. The vendor claims only 17 watts when at rest.

My plan is that this will be a printer & backup server but the backup drive will be a USB drive that will only be turned on when needed so I want the box run without a HDD if possible.

My concern is the limited write cycle life of FLASH drives.  I bought the best quality I could but I still want to preserve it as long as possible.  I formatted it as ext2, for example, to stop the journeling writes of ext3 or ext4.

Has anyone created a check list of configuration settings that will give the flash the longest life possible.

I've been wondering what to do about a swap area too.

TIA

---

### Post by efflandt on 2010-11-05
Swap is really only needed if you do not have enough RAM or want to hibernate (>= RAM), it is not needed for suspend.

You could use **tmpfs** for /tmp and /var/tmp.  But then if you do something that uses more /tmp than you have RAM (making iso or ripping disks), you may need swap.  For tmpfs in /etc/fstab:

tmpfs /tmp tmpfs rw 0 0
tmpfs /var/tmp tmpfs rw 0 0

If you do have swap, you can set **vm.swappiness** to 1 to minimize its use. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Add **noatime** to options for mounting CF partitions (options are comma separated list in /etc/fstab).  See **man fstab**

---

