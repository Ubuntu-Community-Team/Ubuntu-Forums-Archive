---
title: "Can't boot after recovering backup"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by incognitus0 on 2010-11-12
I installed Xubuntu 10.10 on a 16 GB pendrive with full disk encryption using the alternate installer. The installation process was quite time consuming so I made a backup booting from the standard live CD with something along these lines

dd if=/dev/sdb conv=noerror,sync | pv | gzip -c -9 > foobar.img.gz

The pendrive booted fine for a couple of days and BTW it was quite good performance-wise, but I decided to scrape it off and start from the backup, so I run

gunzip -c foobar.img.gz | pv | dd of=/dev/sdb conv=sync,noerror

Now upon boot I am getting

error: hd0,msdos1 write error.

After a while the login screen appears:

Unlocking the disk /dev/disk/by-uuid/58a8... (sdb5_crypt) Enter passphrase:

So I enter it, get the OK message

cryptsetup: sdb5_crypt set up successfully

only to get the following prompt

No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) Enter 'help' for a list of buil-in commands.

(initramfs)

How to fix it? Is it possible to do backups of encrypted systems this way or do I have to use different tools for backup operating on the filesystem level for example?

---

### Post by Herman on 2010-11-12
> No init found. Try passing init= bootarg.So what happens when you try booting up with GRUB in CLI Mode?
[GRUB How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  Rescue your System   

The /sbin/init files are in your / (root partition). 
If you still can't boot, try running e2fsck in your / partition. :)

---

### Post by incognitus0 on 2010-11-12
Finally I didn't go the path of searching what's wrong with GRUB, but I figured out that pendrive's firmware made it read-only at some point. I am not sure if it was when I was installing packages related to virtualbox-ose (I thought it got only "error=remount-ro" then) for the first time, it it was  after running dd from a backup file on it or at another point. Now I am unable to shred its content (tried dd and also shred) and set up partitions from scratch (neither in gparted, nor in the installer. I wrote some further details on askubuntu: [http://askubuntu.com/questions/12858/cant-boot-after-recovering-backup/12945#12945](http://askubuntu.com/questions/12858/cant-boot-after-recovering-backup/12945#12945)

Anyway, thanks for reading about my problem. :)

---

