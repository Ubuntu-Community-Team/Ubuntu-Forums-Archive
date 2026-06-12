---
title: "fsck fails while booting Ubuntu"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by CONCORAN on 2008-02-19
Hello All,
I have 4 partitions, first two for XP and Vista. Next two for Fedora and Ubuntu with Ubuntu in logical partition. I boot the machine using NT loader.
I recently removed fedora (deleted the partition) and installed it again, at the same place. Fedora boots fine, but ever since, I get fsck failure (error 8 ) when booting Ubuntu. After I press ctrl+alt+del, Ubuntu boots just fine.  

Here's the log from /var/log/fsck/checkfs
fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=740b8a34-acca-43c0-a247-00c04ab15435'
fsck died with exit status 8

Here's Ubuntu's menu.lst (ubuntu section only)
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1cb9ddf5-9b46-4226-9959-ab3081913c75 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

I suspect something has changed with respect to UUID of the partition after deleting and recreating fedora partition. I tried replacing UUID section with proper partition name (/dev/sda6), but to no avail.

Is there a way I can fix the problem?

Thank you all in advance.

---

