---
title: "clear syslinux? clear bootable USB"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by lcs81 on 2009-11-30
i got a post at [http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html/comment-page-3#comment-17738](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html/comment-page-3#comment-17738)

on how to create a USB bootable UBUNTU for installation and it is working after i try.
 
However, after syslinux -ma usb:, my usb is bootable. 

Now i wish to use my usb drive for my normal daily usage instead of bootable for installtion.

How do i clear the 'bootable usb' to become unbootable?

After i deleted all the contain in the USB, the USB still able to boot with "SYSLINUX 3.83 .....". How do i celar this? Can i use the syslinux to clear? I do not keep formating my USB stick.

---

### Post by darkod on 2009-11-30
Can this help you:
[http://www.tuxation.com/mbr-tricks-with-linux.html](http://www.tuxation.com/mbr-tricks-with-linux.html)

Look under Erasing the partition table. They have used the term partition table but that command will erase the first 512bytes which also hold the boot process.

Use at your own risk!!! I just googled the link, haven't tried it. :)

Make sure you specify your usb stick as target, not your hdd.

---

### Post by lcs81 on 2009-11-30
Well, is there a way to do it in windos box instead?

---

