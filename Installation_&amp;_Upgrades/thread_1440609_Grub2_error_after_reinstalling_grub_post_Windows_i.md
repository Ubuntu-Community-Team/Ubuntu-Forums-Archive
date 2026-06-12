---
title: "Grub2 error after reinstalling grub post Windows install"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by heatpumpcontrol on 2010-03-27
I'm using the Live CD and have followed steps to recover grub2 after XP install. (damn Windows)!

Upon rebooting I get the grub> prompt with no where to go. Upon installing grub via the Live CD I get this:

> root@ubuntu:~# sudo grub-install --root-directory=/mnt/ /dev/sda
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
root@ubuntu:~#

Any help?

Update:
When I do this [link]("http://linux.shocr.com/linux-blog/ubuntu-live-cd-repair-grub2.html"), upon doing the 

> sudo chroot /mnt

I get this:

> root@ubuntu:~# sudo chroot /mnt
chroot: cannot run command `/bin/bash': Exec format error


Help

---

### Post by heatpumpcontrol on 2010-03-29
For anyone that might need this useful tip:

I fixed it by using the Alternate CD. Followed the prompts to repair the system and then to repair grub.

Thanks to all that responded. I praise the Ubuntu community all the time to get others to convert and this is how I'm repaid. Wow!

---

