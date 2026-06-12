---
title: "Full install of Ubuntu on a flash drive?"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by aring on 2011-09-07
I'm trying to get a full install (or something close that at least isn't stuck in root) on a 16GB flash drive I have so that my development environment will be portable.  I'm relatively new to the Linux world, so I'm not sure how to go about this, or for that matter if there is a reason why this won't work correctly.  Suggestions and pointers would be greatly appreciated.  Thanks.

Andrew

---

### Post by haqking on 2011-09-07
> **aring said:**
> I'm trying to get a full install (or something close that at least isn't stuck in root) on a 16GB flash drive I have so that my development environment will be portable.  I'm relatively new to the Linux world, so I'm not sure how to go about this, or for that matter if there is a reason why this won't work correctly.  Suggestions and pointers would be greatly appreciated.  Thanks.

Andrew


[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

last modified 5 days ago so should be good.

hope it helps

---

### Post by oldfred on 2011-09-07
With 16GB you can do full install just like any install to a second drive with a few extra settings to reduce writes and make the flash drive somewhat better. I have a full install in 8GB, no swap and 8GB just for data on my 16GB flash drive.  I was also testing gpt so I used that instead of MBR, so I had to add one tiny partition for bios_grub.


See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

---

