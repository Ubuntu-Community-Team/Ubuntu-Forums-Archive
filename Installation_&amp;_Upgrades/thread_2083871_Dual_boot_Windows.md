---
title: "Dual boot Windows?"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by nathan.the.sane on 2012-11-13
I guess this is the proper forum section...

I just installed Ubuntu on the entire disk. My plan was to use wine to run Guild Wars 2 but it's not cooperating so now I'm wondering if there is a relatively painless way to sneak a Windows 7 partition back on without reinstalling Ubuntu all over again. Here is my partition layout:

/dev/sda1       230M   58M  161M  27% /boot
/dev/sda2        19G  3.6G   14G  21% /
/dev/sda6       9.2G  150M  8.6G   2% /tmp
/dev/sda7       878G  132G  702G  16% /home
/dev/sda5       2.8G  870M  1.8G  33% /var

All ext3. Also, /dev/sda3 is a 10G swap partition. Can I resize/move stuff to make room for Windows, or should I just bite the bullet and install windows, then Ubuntu again?

---

### Post by oldfred on 2012-11-14
It sounds like you have used all 4 primary partitions. As the extended is also a primary.
Windows will only boot, install, or repair a primary partition (sda1 thru sda4) formatted NTFS with the boot flag.

If dual booting you may also want a separate shared NTFS data partition.

If you have decent hardware you might want a Virtual install. May not be quite as fast but then you do not have to reboot.

But I am not sure you need all the extra system partitions.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

