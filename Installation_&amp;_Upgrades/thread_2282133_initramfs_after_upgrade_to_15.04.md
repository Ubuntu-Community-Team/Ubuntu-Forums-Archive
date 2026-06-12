---
title: "initramfs after upgrade to 15.04"
date: 2015-06-12
forum: Installation &amp; Upgrades
---

### Post by ddhuy on 2015-06-12
My laptop (Thinkpad) doesn't boot any more, neither into Ubuntu, or Windows 8. I tried to upgrade from 14.10 to 15.04 using a bootable USB, but since there were a lot if issues after the install I tried a clean install, also from Live USB. After this I cannot boot and get a grub command line. I have tried these commands I found in another thread:

search -f /vmlinuz
search -f /sbin/init
linux (hd0,1)/vmlinuz root=/dev/sda1
initrd (hd0,1)/initrd.img
boot

But then I get the BusyBox initramfs.

I cannot boot the live USB any more, it now gives an error while booting, even though it worked fine before (I used it to do the install). The boot sequence ends with the error:

end Kernel panic - not syncing: VFS: Unable to mount root fs in unknown-block(0,0)

So I cannot boot a Live Ubuntu and cannot boot into Windows either. I'm completely stuck!

---

### Post by ddhuy on 2015-06-12
These are the two posts I used to find how which commands to use on the grub command line:

[http://ubuntuforums.org/showthread.php?t=2104998](http://ubuntuforums.org/showthread.php?t=2104998)

[http://ubuntuforums.org/showthread.php?t=2264731&highlight=grub+command+line](http://ubuntuforums.org/showthread.php?t=2264731&highlight=grub+command+line)

I added these lines, but the result is the same: initramfs

grub> insmod normal
grub> normal

---

### Post by ddhuy on 2015-06-12
I managed to get into Windows and am making a new bootable USB. Hope to be able to fix issues from Live Ubuntu.

I'll try to install Ubuntu 15.05 again, but this time configure partitions manually, guessing that the standard option to install over existing Ubuntu is how my grub got messed up.

---

