---
title: "netinstall?"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by vh1 on 2005-11-02
is there any way I can do a netinstall of breezy?

I'm asking because I have no wishes to burn any cds (I'm waiting for my shipment of breezy discs, 5 weeks and counting) or to juggle floppy disks

I've tried downloading vmlinuz and initrd.gz from here ([ftp://ftp.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/cdrom](ftp://ftp.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/cdrom)) and putting them on my boot partition

I edited grub's menu.lst file, putting in proper paths, and the proper options. and when I boot into the install from grub everything works fine, it's when the installer checks for the cdrom that I get stuck. it complains that it cannot mount the cdrom, because obviously there is no disc in the tray. and I can't do much of anything else after that, besides execute a shell, or try and mount the cdrom again.

---

### Post by Schmots on 2005-11-02
That I know, there is no way to do a cdless install.  Even Gentoo that lets you install via ssh you have to boot off somekind of live cd.

---

