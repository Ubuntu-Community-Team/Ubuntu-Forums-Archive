---
title: "Fresh 14.04.1 Installation Failure"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by Jecht220 on 2014-09-21
I am having issues installing Ubuntu 14.04.1 LTS onto my computer.  In the /var/log/apt history.log file, this is what it says:

> Start-Date: 2014-09-21  15:45:46
Purge: apt-clone:amd64 (0.3.1~ubuntu11), kpartx:amd64 (0.4.9-3ubuntu7), lvm2:amd64 (2.02.98-6ubuntu2), libgtkmm-2.4-1c2a:amd64 (2.24.4-1ubuntu1), archdetect-deb:amd64 (1.95ubuntu2.1), firefox-locale-es:amd64 (31.0+build1-0ubuntu0.14.04.1), gir1.2-json-1.0:amd64 (0.16.2-1ubuntu1), ubiquity-casper:amd64 (1.340), casper:amd64 (1.340), ubiquity:amd64 (2.18.8), lupin-casper:amd64 (0.55), cryptsetup-bin:amd64 (1.6.1-1ubuntu1), gir1.2-timezonemap-1.0:amd64 (0.4.1), dmraid:amd64 (1.0.0.rc16-4.2ubuntu3), python3-pam:amd64 (0.4.2-13.1ubuntu3), libdmraid1.0.0.rc16:amd64 (1.0.0.rc16-4.2ubuntu3), gparted:amd64 (0.18.0-1), language-pack-zh-hans-base:amd64 (14.04+20140707), language-pack-es-base:amd64 (14.04+20140707), language-pack-gnome-es-base:amd64 (14.04+20140707), libnss3-1d:amd64 (3.15.4-1ubuntu7), ubiquity-ubuntu-artwork:amd64 (2.18.8), libcryptsetup4:amd64 (1.6.1-1ubuntu1), gir1.2-xkl-1.0:amd64 (5.4-0ubuntu1), watershed:amd64 (7), libecryptfs0:amd64 (104-0ubuntu1), rdate:amd64 (1.2-5), reiserfsprogs:amd64 (3.6.24-1), language-pack-gnome-es:amd64 (14.04+20140707), firefox-locale-zh-hans:amd64 (31.0+build1-0ubuntu0.14.04.1), linux-signed-generic:amd64 (3.13.0.32.38), linux-signed-image-3.13.0-32-generic:amd64 (3.13.0-32.57), keyutils:amd64 (1.5.6-1), xfsprogs:amd64 (3.1.9ubuntu2), sbsigntool:amd64 (0.6-0ubuntu7), ubiquity-slideshow-ubuntu:amd64 (83), libdevmapper-event1.02.1:amd64 (1.02.77-6ubuntu2), ecryptfs-utils:amd64 (104-0ubuntu1), metacity:amd64 (2.34.13-0ubuntu4), linux-signed-image-generic:amd64 (3.13.0.32.38), kpartx-boot:amd64 (0.4.9-3ubuntu7), ubiquity-frontend-gtk:amd64 (2.18.8), python3-icu:amd64 (1.5-2ubuntu4), cifs-utils:amd64 (6.0-1ubuntu2), cryptsetup:amd64 (1.6.1-1ubuntu1), language-pack-gnome-zh-hans-base:amd64 (14.04+20140707), libdebian-installer4:amd64 (0.88ubuntu5), dpkg-repack:amd64 (1.37), language-pack-zh-hans:amd64 (14.04+20140707), btrfs-tools:amd64 (3.12-1), language-pack-gnome-zh-hans:amd64 (14.04+20140707), localechooser-data:amd64 (2.49ubuntu5), language-pack-es:amd64 (14.04+20140707), user-setup:amd64 (1.48ubuntu2), jfsutils:amd64 (1.1.15-2.1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2014-09-21  15:46:11

During the installation, it also gives me a "subprocess installed post-installation script returned error exit status 1" error that I'm pretty sure has something to do with initramfs-tools (it's that part of the installation that always crashes).  Also, there is plenty of room on all drives, trying to install it to a 250 GB SSD.

Also, I think what I want is the partitions set up as a 30 MiB /boot partition, a 1 GB swap, and a 30 GB OS partition, with the remainder available for something like /home or app installation or something.  If there is a smarter way to set this scheme up, I'd appreciate advice on that.  Thanks.

---

### Post by ubfan1 on 2014-09-21
Drop the boot partition.  It's too small anyway, but you will always find yourself running out of space on it, so just "Don't do that".

---

### Post by Jecht220 on 2014-09-22
Understood, but is there a good way to address this error?

---

### Post by ubfan1 on 2014-09-22
You may simply be running out of space on the 30M /boot.  That may be enough for one kernel (or may not), but is certainly will be too small for any kernel updates.

---

### Post by Jecht220 on 2014-09-22
This occurs in all forms when I try to install though, even when I use the shortcut option of "using the entire drive" rather than the "something else" option.

---

### Post by ubfan1 on 2014-09-22
I've only installed three times to an SSD, but the devices were new -- never had any problems beyond the expected UEFI/grub install confusion.
Is the SSD new?  If not, was fstrim ever run on it?  I'm not sure, but it seems the SSD can get into a state in which writes fail even when the filesystem thinks there is plenty of space.  Are you running with secure boot enabled?  That might make a difference on some machines which do not follow the UEFI spec very closely.  After a successful install, I did make some tweaks like I would on a flash memory install, moving heavily written locations like /tmp and /var/log into a ram disk.  I use a 300M EFI partition, 25G partitions for various roots, and a big data partition. If your SSD is in an external enclosure and you might want to boot it off a non-UEFI machine, you could add a 1M grub-bios partition (I assume you are using gpt partitioning) and install the grub-pc too.  C.S.Cameron has written up some USB howtos which pretty much apply to SSDs also.

---

