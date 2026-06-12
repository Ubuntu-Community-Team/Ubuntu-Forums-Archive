---
title: "Live USB- no write permission"
date: 2012-08-18
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2012-08-18
Hi,
Just completed a persistent live Ubuntu (12.04-386) on  a (large) USB memory which contains an additional 18GB ext4 partition (besides the casper 4GB FAT32 one).
While the additional partition gets mounted, the default user can't write (save files) in that partition, nor can he write in home (although he CAN write in home/Documents..).

How can I get write permissions to all locations?
Another question, how do I create a persistent user with PW?

Thanks

---

### Post by oldfred on 2012-08-18
I do not know much about persistent installs, but if you want all the features of an install why not a full install on the flash drive? I have 12.04 64 bit running more as a test in 8GB on a 16GB flash drive with the rest for data.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

### Post by efflandt on 2012-08-18
Whether you can write to that other ext4 partition depends upon who owns directories and files on it, and permissions of those directories and files.  Whether someone can put files on the root of that partition may also depend upon how it is mounted.

You can add users with passwords to live/install iso with persistent data.  However, that is primarily intended for testing and installation.  It will still boot as default user "ubuntu" with no password.  That seems to be impossible to change without remastering the iso first, since the system boots from a fixed squashfs file system before persistent data is mounted.  That is also why you cannot add video drivers or update kernels on it, because that is all on the fixed initial boot.

---

### Post by mibadt on 2012-08-18
Thanks,
I did not install on the USB, as I would like to use it on multiple, different PCs (different hardware).
Thanks

---

### Post by oldfred on 2012-08-18
If you do not install any proprietary drivers, a full install will be like a liveCD and work just about anywhere. Of course some systems may need a proprietary driver to work or to work well.

---

