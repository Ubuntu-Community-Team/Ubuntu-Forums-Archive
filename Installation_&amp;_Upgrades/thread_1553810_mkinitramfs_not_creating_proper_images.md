---
title: "mkinitramfs not creating proper images"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by HeadHunter00 on 2010-08-15
well, the title says it all, mkinitramfs isnt creating proper initrd images. it used to work properly in karmic, but now i get an error saying 5: scripts/functions not found. wat does that mean? oh and also, when i boot into the new custom kernel, i am thrown into initramfs shell

---

### Post by HeadHunter00 on 2010-08-15
this isnt a bump, just a message to get attention.

---

### Post by HeadHunter00 on 2010-08-15
I found the solution at launchpad. It seems that some packages interfere with initramfs-tools, so to solve the problem, you simply remove them using: sudo apt-get remove realpath bootcd-i386 bootcd bootcd-mkinitramfs fdutils realpath bootcd-i386 bootcd bootcd-mkinitramfs bootcd-backup fdutils bootcd-i386 bootcd bootcd-mkinitramfs bootcd-backup bootcd-i386 bootcd libaio1 seabios bridge-utils qemu-kvm vgabios qemu-common kernel-package bootcd-mkinitramfs bootcd-i386 bootcd-mkinitramfs bootcd-i386 bootcd bootcd-mkinitramfs cryptsetup realpath bootcd-i386 bootcd fdutils bootcd-i386 bootcd bootcd-i386 bootcd

---

