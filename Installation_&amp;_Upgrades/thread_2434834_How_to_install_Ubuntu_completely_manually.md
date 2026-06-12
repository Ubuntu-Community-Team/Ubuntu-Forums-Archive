---
title: "How to install Ubuntu completely manually?"
date: 2020-01-11
forum: Installation &amp; Upgrades
---

### Post by mpb_ on 2020-01-11
Is anyone aware of a guide or tutorial that explains how to install Ubuntu completely manually?  (In other words: from the command line without the use of any opaque "installer" programs.)

I'm looking for something along the lines of the Arch Linux Installation guide:
[https://wiki.archlinux.org/index.php/Installation_guide](https://wiki.archlinux.org/index.php/Installation_guide)

My goal is to boot a live Ubuntu environment (possibly the Desktop .iso) and then, from the command line, manually perform an installation of Ubuntu.

I would expect such a guide to contain (at least) the following steps:

1) partition disks
2) format partitions
3) mount partitions
4) install system files (possibly via debootstrap)
5) chroot into the new installation
6) install any additional needed packages
7) install a kernel
8) configure, build and install the init ram disk
9) install a boot loader

I know how to do 1-5.

I expect 6-7 to be pretty straightforward.

It is really 8 (building initrd) that I am curious about.  I anticipate using an unencrypted /boot partition, plus a LUKS encrypted root btrfs partition.

9 is probably fairly straightforward.

Step 8 is usually handled by one of Ubuntu's installers (desktop, live-server, server, or net boot).  But due to some specific technical constraints, I would like more transparency and control, so I am considering trying a fully manual installation.

Before I try to discover how to do a manual installation via experimentation, I figured I would ask to see if anyone know of any existing guides or documentation that would be helpful.

Thank you.

---

### Post by Impavidus on 2020-01-12
Step 4 also includes configuring those system files, in particular your software sources, /etc/fstab, /etc/default/grub, files like that. There you can also choose settings for initramfs-tools.

Step 7 is included in step 6. The kernel is installed from a package from the repositories, just like everything else.

Step 8 is included in step 7. Whenever a new kernel is installed, the init ram disk has to be rebuild and installed. This happens regularly with kernel upgrades, so the necessary commands are included in the installation scripts of the kernel package.

Also, don't forget to set up user accounts. Maybe on Arch it's standard to create only a root account during installation and user accounts later, but on Ubuntu it's standard to keep the root account locked and create an admin user account during installation.

---

### Post by mpb_ on 2020-01-12
Okay, so I did the following:

1) Booted the Desktop .iso.
2) Created a LUKS-encrypted ext4 root partition and a separate /boot partition.
3) Ran debootstrap
4) chrooted in ran apt-get install linux-image-generic

Step #4 installed grub.

I then rebooted.  Grub boots.  Grub can boot the kernel and the initrd.

However, the initrd cannot find my encrypted root partition by its UUID.  I suspect this is because the initrd does not know that the root partition is inside a LUKS encrypted partition.

Does anyone know which configuration file(s) I need to edit so that the initrd gets built with the ability to cryptsetup luksOpen my encrypted LUKS partition?

Thank you.

---

### Post by mpb_ on 2020-01-12
I remembered that in the past I have seen a package called cryptsetup-initramfs.
This package contains a file:
/usr/share/doc/cryptsetup-initramfs/README.initramfs.gz

The above file appears to contain the relevant instructions.

---

### Post by mpb_ on 2020-01-13
Here is my installation script:
[https://github.com/parke/minibuntu/blob/master/minibuntu.sh](https://github.com/parke/minibuntu/blob/master/minibuntu.sh)

---

