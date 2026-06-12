---
title: "Debian Sid chrooted in Ubuntu 10.10"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by Jack Ryan on 2012-01-14
Hi all-

I have a semi- production workstation currently running 10.10. I'd like to try out some newer features (GNOME3, Linux 3.1, etc.) during off- hours, but I can't really afford much downtime in my main system. I've set up sid in chroot with debootstrap, and I'd like to make this bootable. 

I *could* of course, create a new partition, but I'm using a 60GB SSD and I'd really rather not fool around with moving files back and forth constantly. 

My question, then, is how do I edit Grub 2 to boot the newer linux image with /sid as the root filesystem? I've seen a few tutorials about cross-installation, but nothing that didn't require a new partition. What additional configurations will I have to make?

Thanks in advance.

---

### Post by dino99 on 2012-01-15
you might experiment with vmware or virtualbox to avoid headaches with testing/tweaking :)

---

### Post by Jack Ryan on 2012-01-15
We've done a good deal with that, but we're most interested in graphics capability and filesystem performance. Something we can't really extrapolate from virtualmachines in good faith.

---

