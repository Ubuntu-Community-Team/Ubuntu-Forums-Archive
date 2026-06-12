---
title: "Boot record not found"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by coolclassic on 2005-10-14
When trying to reboot after initial install harddrive fails to boot: The message is- Boot record not found-.

During the initial install grub was written to the hd this was witnessed by the progress bar.

How do I get the new installation to boot?

Harddrive is maxtor 80gb is the size the problem?

---

### Post by shenki on 2005-10-14
try booting from a live cd; see if it can mount any partitions from the hard drive.

If it can, it means your linux install is there, but grub didn't quite install right.

To reinstall it, type 'sudo grub-install --root-directory=/boot /dev/hda' to install to the first sector of the primary ATA HDD.

---

### Post by coolclassic on 2005-10-14
Checked the partions and grub is installed.

---

### Post by coolclassic on 2005-10-14
Still not solved my boot problem so here is my menu.1st file if it helps
## ## End Default Options ##

title  Ubuntu, kernel 2.6.12-9-386 
root  (hd0,0)
kernel  /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd  /initrd.img-2.6.12-9-386
savedefault
boot

title  Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root  (hd0,0)
kernel  /vmlinuz-2.6.12-9-386 root=/dev/mapper/Ubuntu-root ro single
initrd  /initrd.img-2.6.12-9-386
boot

title  Ubuntu, memtest86+
root  (hd0,0)
kernel  /memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

