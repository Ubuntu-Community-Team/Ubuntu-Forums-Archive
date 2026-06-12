---
title: "Installation does not see hard drive"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by madm0nk on 2009-12-07
Ok I installed vista creating a seperate partition for it (150GB HD 75 for windoze and 75 for ubuntu) and windoze install went through without a hitch. When I try and install Ubuntu 9.10 the installation does not see the hard drive. But if I boot the live cd and run gparted everything looks fine. I have the NTFS partition for windoze and unallocated space for the rest. The HD is a Seagate ST3200822AS. I have searched everywhere on this forum and google and found no real help. In the BIOS the drive is SATA (IDE not AHCI). Should I change it to AHCI or will that jack up the windoze installation? Also I tried installing 9.04 instead and had the same problems.

---

### Post by Ginsu543 on 2009-12-08
Don't change your SATA setting to AHCI because it will prevent your Windows installation from booting (in order for Windows to work under AHCI you must install Windows after installing AHCI drivers by pressing F6). Instead, try this:

1) Boot into a live session using the Live CD (Try Ubuntu without installing)
2) Open Terminal and type "sudo apt-get remove dmraid" (without quotes)
3) Close Terminal and run the installer by double-clicking on its icon

If all goes well, the installer should now be able to see your hard drive.

---

### Post by madm0nk on 2009-12-11
> **Ginsu543 said:**
> Don't change your SATA setting to AHCI because it will prevent your Windows installation from booting (in order for Windows to work under AHCI you must install Windows after installing AHCI drivers by pressing F6). Instead, try this:

1) Boot into a live session using the Live CD (Try Ubuntu without installing)
2) Open Terminal and type "sudo apt-get remove dmraid" (without quotes)
3) Close Terminal and run the installer by double-clicking on its icon

If all goes well, the installer should now be able to see your hard drive.

That worked thanks.

---

### Post by Ginsu543 on 2009-12-11
Excellent!

---

