---
title: "Can I boot from MBR without a bootloader"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by dajasc on 2010-01-17
This is a somewhat weird situation.  I have an old laptop and am trying to install Xubuntu.  It has no CD drive and cannot boot from USB.  It can however boot from PXE.  

I have successfully installed Xubuntu this way.  However, it will not boot after install.  I'm not sure what happens but somehow after GRUB (or LILO, I have tried both) something happens and it can't find the hard drive.  (This is not specific to Xubuntu, anything that requires a bootloader behaves the same)  After trying a bunch of things I installed freeBSD which has the option of booting from the MBR rather than installing a bootloader like GRUB.  It boots into freeBSD without any problem.  The problem is I don't want to use freeBSD.

I tried installing Xubuntu without installing GRUB but it won't boot at all.  So the complete Xubuntu install is on the hard drive but I don't know how to fix the MBR to get it to boot.  I am able to netboot into something like Tiny Core Linux.  Is there any way to boot into that and then fix the MBR so that I can boot the Xubuntu installation?

---

### Post by dajasc on 2010-01-18
Oddly, the Debian Lenny installer worked without any problem and the system will now boot into a Gnome desktop.

---

### Post by dajasc on 2010-01-18
Oddly, the Debian Lenny installer worked without any problem and the system will now boot into a Gnome desktop.

---

