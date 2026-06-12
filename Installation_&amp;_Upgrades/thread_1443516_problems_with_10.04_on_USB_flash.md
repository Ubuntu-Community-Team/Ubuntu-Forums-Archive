---
title: "problems with 10.04 on USB flash"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by marvin4242 on 2010-03-31
Hi,
(I tried below things several times from scratch, so it is not a one time problem)
I installed live 10.04 on my USB. I can boot it, configure wifi etc. I can reboot and see the changes. Then I do a backup of the flash to my windows machine.
When I do any update from update manager (does not matter which package), when I reboot, I always get error, cannot find live filesystem.
Then I go to windows machine, don't touch caper-rw, copy casper/initrd.gz and casper/vmlinuz (just these two) to my usb flash and then I can boot from it again, I see those packages I installed to be installed. 
In short - every time I install something via update manager, casper/initrd.gz and casper/vmlinuz get updated and I cannot boot.

I tried to find something about this, no luck.

---

### Post by marvin4242 on 2010-04-02
OK, I found the solution, looks like bug to me, but as I have no idea against which package to file it....

Problem is, when you do for example kernel upgrade (beta 10.04 comes with 2.6.32-16) using Update Manager (to 2.6.32-19), it will update /cdrom/casper/initrd.gz. But /cdrom/casper/vmlinuz and /cdrom/casper/initrd.lz are not updated. When I created /scripts directory and copied casper-functions and functions (from `locate casper-functions` directory) to it, then update-initramfs was able to update vmlinuz and initrd.lz as well and reboot went well, ending up with correct 2.6.32-19 kernel.

Another important note, word of caution - when you create persistent file on USB, don't use the whole free space for it, otherwise vmlinuz cannot be updated and warning about no space left on device flashes for a very short time only.

---

