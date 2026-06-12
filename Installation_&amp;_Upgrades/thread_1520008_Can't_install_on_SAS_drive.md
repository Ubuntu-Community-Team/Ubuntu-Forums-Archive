---
title: "Can't install on SAS drive"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2010-06-29
I have a machine containing a 15k RPM SAS drive connected to an Intel SASWT4i controller and a SATA drive connected to the onboard SATA controller. When I boot off the 10.04 amd64 DVD and choose the option not to install Ubuntu but to run it off the DVD, when the Gnome desktop appears I can run Gparted and see both the SAS and SATA disks (and partition them), and lspci shows "SCSI storage controller: LSI Logic / Symbios Logic SAS1064ET PCI-Express Fusion-MPT SAS (rev 08)". However, when I choose the desktop icon to install Ubuntu to the hard disks, when I get to the Prepare Disk Space dialog of the install, only the SATA disk is shown as an option for installing to.

I also booted off the DVD and chose to run a text mode install, but when I get to the partitioning part of that, I again only have the SATA disk as a option for the install.

Is it possible to install to the SAS disk?

---

