---
title: "Install ubuntu gnome as triple boot"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by andy14 on 2013-11-07
Currently I have win7 and opensuse dual boot.  I have already 4 physical partitions. At the moment my gparted is below
[http://postimg.org/image/ul32kumhl/](http://postimg.org/image/ul32kumhl/)

I wish to install ubuntu gnome keeping my win7 and opensuse.

Booting with live CD, installer allow me to install along side and shrink win7
[http://postimg.org/image/3xzi4sqxl/](http://postimg.org/image/3xzi4sqxl/)

however the installer show the new ubuntu partition as sda3 (but which is one of my existing windows recovery partition)?  I would like to check what the installer would do if I click 'install now'.

1.  assume it expand my current extended partition sda4 at the start (Left hand side)?
2.  would ubuntu gnome be installed in the space created in (1)?
3.  if it install successfully what would I see in the grub menu?  would there be new grub in ubuntu partition?
4.  wish to have some comfort that my win7 and opensuse should still work?

Thank you.

---

### Post by grahammechanical on 2013-11-07
My advice would be 1) use Windows utilities to defrag the Windows partition at least twice. 2) use Windows utilities to shrink the Windows 373 GB partition by 10 - 20 GB. 3) Make doubly sure that Windows and Opensuse load. 4) Use the Something else option to (a) expand the extended partition, sda4, to take up the unallocated space (10 - 20GB) (b) create a new partition of the unallocated space (c) install Ubuntu Gnome into the new partition. Where do you want Grub to go? You will have to tell the installer that you want it in the intended Ubuntu Gnome partition if that is what you want. The installer will by default install it into the MBR of sda and overwrite any boot loader that is already in there.

---

### Post by fantab on 2013-11-07
> **grahammechanical said:**
> My advice would be 1) use Windows utilities to defrag the Windows partition at least twice. 2) use Windows utilities to shrink the Windows 373 GB partition by 10 - 20 GB. 3) Make doubly sure that Windows and Opensuse load. 4) Use the Something else option to (a) expand the extended partition, sda4, to take up the unallocated space (10 - 20GB) (b) create a new partition of the unallocated space (c) install Ubuntu Gnome into the new partition. Where do you want Grub to go? You will have to tell the installer that you want it in the intended Ubuntu Gnome partition if that is what you want. The installer will by default install it into the MBR of sda and overwrite any boot loader that is already in there.

+1.

Just to expand on the Grub part- you already have grub from openSUSE. By default Ubuntu will replace that GRUB with its own (and this will NOT create any issues or problems). However, if you don't want Ubuntu to replace GRUB then install Ubuntu's GRUB to its own partition. But if you install ubuntu-grub to its own partition then after installing Ubuntu you will have to boot into openSUSE and update grub there for Ubuntu to appear as option in Grub-Menu. And do this everytime there is an Kernel upgrade in Ubuntu.

If you install Ubuntu's grub then you will have to update-grub in Ubuntu whenever there is a kernel upgrade in openSUSE.

EDIT: To manage ubuntu's grub manually [Check this out]("http://ubuntuforums.org/showthread.php?t=2076205").

---

