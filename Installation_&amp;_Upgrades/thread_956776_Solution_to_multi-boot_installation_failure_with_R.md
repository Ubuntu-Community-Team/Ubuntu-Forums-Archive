---
title: "Solution to multi-boot installation failure with Red Hat (and maybe other OSes)"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by xit77 on 2008-10-23
Symptom is as below:

Installed CentOS first, and then tried to install Ubuntu.
Installation continues until about 80-90% and suddenly X restarts. (not reboot)
/boot directory is incomplete (grub directory and initrd is missing)
When reboot, grub error occurs.  
Tried 7.01 and 8.04, both of which failed.

I've spend several hours struggling with this problem, and I finally found out why:

When CentOS (and also other RedHat linux series using anaconda as installation program, I suspect) is installed, anaconda formats (ext2/3) partitions and labels them with names that includes some special characters (e.g., /1).  Ubuntu installer recognize them at first, but later, fails to locate it under /dev/disk/by-label because '/' is illegal character for filename and hence transformed into 0x2f by kernel (e.g., /dev/dsik/by-label/0x2f1), but Ubuntu installer locate it without transformation (e.g., /dev/disk/by-label//1)

Solution is:

Boot into RedHat (after restoring grub if needed)
Change partition labels by

  e2label <device> <new-label>
  (e.g., e2label /dev/sda1 root)

for each partition whose label contains '/'.
Edit /etc/fstab and /boot/grub/menu.lst to reflect the change.
Reboot to make sure RedHat still works.
Now, install Ubuntu.

Clearly, this problem can occur with other preinstalled filesystems, distributions, or OSes,
and  should be considered as a bug in Ubuntu installer.

I hope someone save his/her time.

---

