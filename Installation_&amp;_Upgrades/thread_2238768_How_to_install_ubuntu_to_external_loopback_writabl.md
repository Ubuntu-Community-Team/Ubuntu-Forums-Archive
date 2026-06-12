---
title: "How to install ubuntu to external loopback writable encrypted file?"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by dbpalan on 2014-08-09
This is a challenging question.  I have a 32GB SD card that wish to use 8GB for ubuntu installation and the rest 24GB for my camera.  As a result ubuntu need to be installed in:

* An SD card with single partition in a FAT32 file system
* Loopback file for boot partition
* Loopback file for other partitions, encrypted
* Full installation or base on a light weight boot ISO loopback, but not a live-CD loopback

Is this possible?  The closet thing I found is WUBI but it requires Windows (which I have quitted!) and has been certified.

---

### Post by oldfred on 2014-08-12
Wubi does not require Windows, and can be booted with grub, but I am not really suggesting that.
I think this was more just to prove a point that you could use grub.

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

Will camera only see the first or only FAT32 partition?

I have used grub2 on FAT32 partition to loopmount the ISO as a live installer. But do not know if that would interfere with your camera using SD card?

Do not know anything about encryption.

---

