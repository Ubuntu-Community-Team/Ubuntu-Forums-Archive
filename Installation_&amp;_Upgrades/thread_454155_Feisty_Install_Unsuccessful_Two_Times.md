---
title: "Feisty Install Unsuccessful Two Times"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by HobbitTR on 2007-05-25
I have unsuccessfully tried to install Feisty two times on my desktop machine.  I am currently running Edgy without any problems whatsoever.  After the first try, I searched the forums and found very little useful information for this noob (2 year Ubuntu user) to understand.  After my first try, I reinstalled Edgy without any problems whatsoever.  I later tried again and this time, I disconnected my second internal (slave) HD just to see if that would take care of the problem.  It still would not boot.  My UUID's match even tho the boot errors say they do not exist.   I am stumped, help please. If you know of a solution, feel free to email me direct and I would appreciate a detailed list of HOW TO...:(

the error messages I get are as follows and I will attach some documents including fstab.
------------------------------------------------------------------------------------------------------------------
cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/54764a11-fdbb-4c57-8ee5-c79a638f69ec does not exist.

34-432227] Device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA Done.

/bin/sh: can't access tty: job control turned off.

check root=bootarg cat /prob/cmdline or missing modules, devices: cat /proc/modules ls /dev

Waiting for "/sys/devices/pci0000:00/0000:00:03:0/usb1/1-1/1-1.3/1-1.3:1.0/host2/target2:0:0/2:0:0:0/ioerr_cnt" failed

usb-id {2898}:usb-id:unable to access "/block/sdc"
scsi-id {2903}:scsi-id:unable to access "/block/sdc"
scsi-id {2904}:scsi-id:unable to access "/block/sdc"

/bin/sh: can't access tty:job control turned off (initramfs)

---

### Post by Rasymas on 2007-05-25
I just noticed that in order to update to 7.04 you need to have 6.10 Breezy or smth. But I only have 6.06 LTS which is not keen on upgrading to 6.10. Once I run distribution update I get these failed to fetch errors.. Anyone with solution here? 

Thanks in advance ;)

```
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz 302 Found
Failed to fetch http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz 302 Found
Failed to fetch http://theli.free.fr/packages/breezy/./Packages.gz 301 Moved Permanently
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/free/source/Sources.gz Unable to fetch file, server said ‘Failed to open file.  ’
Failed to fetch ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/breezy/non-free/source/Sources.gz Unable to fetch file, server said ‘Failed to open file.  ’

```

---

