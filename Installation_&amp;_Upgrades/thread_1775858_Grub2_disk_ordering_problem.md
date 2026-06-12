---
title: "Grub2 disk ordering problem"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by MartynT on 2011-06-05
Hi,

I recently replaced the motherboard of my system.  Prior to the swap I had 3 HDDs, one with Ubuntu and grub2, one with windows7 and an old one with XP and a wubi install.

When I upgraded I just plugged in the windows7 HDD and reinstalled.

The other day I plugged in the old Ubuntu disk and it works fine if it is the only HDD, but if I also have the Win7 HDD, the grub2 boot gives me the option of Ubuntu or Win7.  Win7 works fine but Ubuntu throws up a /boot mount error, followed by a /home mount error.

I booted in with just the Ubuntu disk, ran update-grub, which modified the /boot/grub/grub.cfg, but on rebooting (with both disks), grub2 seems to still know about/discover both disks and the Ubuntu disk still gives the same errors.

I presume it is just because the disks are in a different location (or different uids).  Is there a software way to fix this, i.e. one that doesn't involve trial and error plugging in disks into different sata ports ?

---

### Post by mikewhatever on 2011-06-05
UUIDs should not change when you add or remove HDDs, but both partition and HDD numbering may. For example, /dev/sda may become /dev/sdb when connected as non-first HDD. I strongly suspect that your Grub setup doesn't use UUIDs at all for the Linux partitions (think that was the case with Ubuntu 8.04). Anyway, to help us help you, please post the contents of your Grub configs.

---

### Post by drs305 on 2011-06-05
Have you checked the /etc/fstab for the Ubuntu installation in question? Do the entries in fstab agree with the new setup? If you are getting error messages about /home it's probably referencing fstab settings.

Using UUIDs, or even better, labels, in fstab helps reduce problems when moving disks around.

---

