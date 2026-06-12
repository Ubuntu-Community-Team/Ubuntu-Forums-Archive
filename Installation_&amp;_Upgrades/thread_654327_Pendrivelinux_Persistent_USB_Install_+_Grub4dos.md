---
title: "Pendrivelinux Persistent USB Install + Grub4dos"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by daddy_fizz on 2007-12-30
Here is the problem I am having.  I currently use my USB drive with one bartpe based recovery disk and one dos based recovery disk.  I wanted to try out Ubuntu on my drive as well (using the pendrivelinux guide) and continue to use my bartpe/dos based recovery disks.  I have followed the guide and can get ubuntu 7.10 to run on my flash drive with no problems.  

I made an entry into the ubuntu startup menu so that I could load up my old grub4dos menu (using grub.exe) that I used before I tried out ubuntu, and run my dos/bartpe disks.  The grub menu will come up fine, but any of the recovery disks will run very much slower then they used to.  (pardon my ignorance but is this becuase some form of the ubuntu kernal is loaded already when I load grub.exe)?  even bringing up the menu takes 5-10x longer then when I had the drive formatted to run these two recovery disks.


I was wondering if either of these solutions would be possible.

1.  Keep the MBR loading syslinux and have it boot directly into grub.exe before any kind of Ubuntu related files are loaded.

2.  Keep my drive the way it used to be (loading grub4dos through boot.ini) and add some kind of entry for my persistent Ubuntu 7.10 install


Thanks for all your help!  I hope to have even more fun with Ubuntu in the future.

---

### Post by daddy_fizz on 2007-12-31
Ok so I got the grub4dos loader to stick around but got the casper-rw partition and the normal fat16 partition setup.

Would anyone know the grub4dos (GRUB) command to load the syslinux command for the persistent install:

from syslinux.cfg

LABEL persistent
  menu label ^Start Ubuntu in USB persistent mode (saves changes) 
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz quiet splash --


if I could get this to boot in grub4dos I would be good to go.  Right now I can get ubuntu to load partially then it hangs, kicks me to a busybox v1.1.3 prompt...

---

### Post by daddy_fizz on 2007-12-31
Ok i got it working :) guess it pays to not give up

can now boot through boot.ini and grldr and then boot into ubuntu...

---

