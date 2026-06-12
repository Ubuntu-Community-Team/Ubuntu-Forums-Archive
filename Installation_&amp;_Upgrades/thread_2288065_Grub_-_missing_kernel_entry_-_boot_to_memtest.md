---
title: "Grub - missing kernel entry - boot to memtest"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by simonmurton on 2015-07-24
After cleaning up old kernels from my default  250Mb boot partition to facilitate kernel upgrade , I forgot to update grub , I then updated and on reboot , straight to memtest . I tried booting to live CD but as yet have not worked out how to create a grub.cfg file which I guess is going to be my solution . I have other computer with the latest ububtu , maybe the solution is to cut/copy/paste a grub.cfg file from one of those onto my broken laptop , where can I find the file ? Is there another way to rebuild/update  grub ? Many thanks SM

---

### Post by VMC on 2015-07-24
This link will help with boot-repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You could examine using the Grub commands, but that's a little more advance.

---

### Post by oldfred on 2015-07-24
Boot-Repair is probably the easiest. And always good to know how to use it. I regularly use it or that really is the first part of it or bootinfoscript to document my system.

But you can chroot into system and update from inside your system.

Or you may be able to manually boot from grub's command line.
If you have a working updated kernel, that would have updated a link in /boot which makes it a bit easier to add your own boot stanza manually.

At grub menu, go to command line and type your own boot. If you know partition, change hd0,5 to correct partition. If not
       ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.

            
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

