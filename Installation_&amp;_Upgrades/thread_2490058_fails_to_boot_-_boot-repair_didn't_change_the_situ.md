---
title: "fails to boot - boot-repair didn't change the situation"
date: 2023-08-21
forum: Installation &amp; Upgrades
---

### Post by lfast on 2023-08-21
I managed to brick my desktop while trying to setup /boot/efi/EFI on a new disk. boot-repair did fix the problem.

Attached are the pastebins from before and after running boot-repair.  I also included journalctl output, since the problem may be in there somewhere. Note: they are labelled .tar just to get around file size limits.

I suspect I wrecked things following these instructions: [https://askubuntu.com/questions/1250199/move-bootloader-or-remove-efi-partition-in-second-drive](https://askubuntu.com/questions/1250199/move-bootloader-or-remove-efi-partition-in-second-drive)
summary:
  edit fstab to set /boot/efi to the new partition
  sudo umount /boot/efi && sudo mount /boot/efi
  grup-install /dev/sda
  update-initramfs -u -k all
  update-grub

My next steps?  Plan to diff the journalctl output to compare boot process before and after my ill-considered changes.

Ubuntu 22.04

---

### Post by lfast on 2023-08-21
Resolved!  
While boot-repair did not work for me, reinstalling did.  

- rename lvm root partition to root_os_old
- reinstall Ubuntu using liveUSB => new lvm partition called root_os 
- after install completes and boots properly ...
- rename lvm partitions
    root_os => root_os_new
    root_os_old => root_os
- reboot and voila!  The original root_os partition is running again with no issues ... so far ...

---

### Post by MAFoElffen on 2023-08-23
Thank you for sharing your solution to this.

It would help others if you marked this as "Solved" (use the Thread Tools link at the upper right) so that others can find it easier, and can help them.

---

