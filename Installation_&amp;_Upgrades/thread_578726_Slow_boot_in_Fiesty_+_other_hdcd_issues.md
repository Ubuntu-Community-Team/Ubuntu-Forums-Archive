---
title: "Slow boot in Fiesty + other hd/cd issues"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by alii on 2007-10-17
Hi, I'm having a few issues with my new Feisty upgrade.

1) My CDRW isn't being detected, but the DVDR is working fine
2) If I boot with my (NTFS) USB drive plugged in all of my (NTFS) partition mountpoints get messed up. My fstab looks like:
[FONT="Lucida Console"]proc /proc proc defaults 0 0
/dev/sdb1 /             ext3            defaults,errors=remount-ro      0 1
/dev/sda1 /Fat32        vfat            defaults                        0 0
/dev/sdb6 none          swap            sw                              0 0
/dev/scd1 /media/cdrom0 udf,iso9660     user,noauto                     0 0
/dev/dvdrw /media/dvdrw udf,iso9660     user,noauto                     0 0
/dev/sda7 /MP3s         ntfs-3g         defaults,locale=en_GB.UTF-8     0 0
/dev/sda6 /Windows      ntfs-3g         defaults,locale=en_GB.UTF-8     0 0
/dev/sda5 /Storage      ntfs-3g         defaults,locale=en_GB.UTF-8     0 0
/dev/sdb5 /Movies       ntfs-3g         defaults,locale=en_GB.UTF-8     0 0[/FONT]

basically all the sda's and sdb's get moved around - very annoying.

3) On booting the system hangs for a few minutes. After pressing Alt+F1 i've found the problem to be at:
[FONT="Lucida Console"]mdadm: No devices listed in conf file were found
[    55.109513] ata2.01 failed to set xfermode (err_mask=0x4)
[    90.908372] ata2.01 failed to set xfermode (err_mask=0x4)
[    126.707236] ata2.01 failed to set xfermode (err_mask=0x4)
[    131.707719] ata2.01 failed to set xfermode (err_mask=0x4)[/FONT]

any ideas?

---

### Post by alii on 2007-10-17
actually all issues seem to have been solved by adding "irqpoll" onto the end of the grub boot line in /boot/grub/menu.lst

weird.

also i've removed both cd/dvd drives from fstab as it seemed rather superfluous.

---

### Post by satbunny on 2007-11-23
Thanks for the irqpoll tip, solved a problem Dell couldn't solve for me.

The problem is wider than Ubuntu, the same problem happens with all LiveCDs, whatever the distro.

I have blogged how I solved the whole Ubuntu install onto a Dell that exhibits this problem here:

[http://tzunder.livejournal.com/2007/11/23/](http://tzunder.livejournal.com/2007/11/23/)

Dell Ubuntu Linux and xfermode (err_mask=0x4)

---

