---
title: "partition shows as full when only 20% used"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2006-11-16
This must be the reason my installation failed.
(See [http://ubuntuforums.org/showthread.php?t=301012](http://ubuntuforums.org/showthread.php?t=301012) )

At the end of a new installation, the Kubuntu installer was unable to install grub's bootloader.  I realize now that my /boot partition which I set up as 40MB, and which only contains 7.2MB of files that the installer put there, is showing as full.

I have no idea why that partition is showing as full, but that's obviously why grub-install is unable to create /grub there.  I tried from the live-cd shell and of course I can't create any directory there either.
/boot is the only thing on /dev/hda5.

du reports the usage of /boot as 7274.

but the output of df is completely screwed up:
```
Filesystem   1K-blocks   Used   Available     Use%   Mounted On
/dev/hda7   19534372   1609836   17924536     9%   /
/dev/hda5      40120     40120          0       100%      /boot
/dev/hda8   19534372   1609836   17924536    9%   /home
/dev/hda10   19534372   1609836   17924536    9%   /mnt/arc
/dev/hdc   19534372   1609836   17924536      9%     /media/cdrom0
/dev/hda5      40120     40120          0       100%      /boot


```

I partitioned the disk as follows:
```

hda1   400MB   fat16      not mounted
hda2    19GB   ntfs        not mounted
hda3  (remainder of disk - extended)
hda5    40MB   reiserfs    /boot
hda6     1GB                  swap
hda7    20GB   reiserfs    /
hda8     2GB   reiserfs     /home
hda9     2GB   reiserfs     not mounted
hda10   15GB   fat32       /mnt/arc
hda11   15GB   fat32       not mounted

```

so the partition table seems to be butchered.  Any ideas?

---

### Post by taurus on 2006-11-16
On my Edgy with two sets of kernels, /boot only uses 20MB so not sure why you ran out of space on your /boot with 40MB although I use ext3 for my /boot while you use reiserfs!  I guess you have to use the LiveCD and mount your /boot, /dev/hda5, and see what takes up all the space there.

---

### Post by r.stiltskin on 2006-11-16
I booted with Knoppix, unmounted, reformatted (again with reiserfs) and remounted /dev/hda5, and, with NOTHING in there, df reports 32840 1k-blocks (82%) used.

So that seems to be the source of my problem.  Is it normal for reiser fs to take 32MB of overhead for a 40MB partition?

---

### Post by taurus on 2006-11-16
Not sure about reiser since I don't use it.  Always use ext3 and never have any problem with it.  I would recommend you set /boot as ext3 and reiser for everything else if you want to use reiser...

---

### Post by r.stiltskin on 2006-11-16
Any particular reason other than disk overhead?

('cause before I read your post, I already repartitioned the disk to give /boot 80mb instead of 40, and started reinstalling the whole works...)


ps: I guess that overhead is normal.  I just checked my Gentoo box & it shows 37MB used in /boot, even though the files there total only about 4.3MB.  I never noticed it before because Gentoo doesn't save as much "junk" in /boot so it never became a problem.

Anyway, that's the solution; just needed more space.  It would be nice if the installer gave a REASON when it failed to install the bootloader.

---

