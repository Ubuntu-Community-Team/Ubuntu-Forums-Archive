---
title: "Using CloneZilla to image a Ubuntu 12.04 machine with UEFI to exact hardware failing"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by applerock79 on 2013-10-10
Hi all,
The title says it all in a nutshell.
On the "new" cloned PC all I get is a "REBOOT AND SELECT PROPER BOOT DEVICE" error when I boot. Original PC (that was used to create the image clone from Clonezilla) works and boots fine. The details:
1. Using latest version 2.1.2-43 of Clonezilla
2. MB is Biostar A880GZ with UEFI (both source and destination PCs have the same EXACT hardware)
3. Windows is not in the picture at all. This is strictly a single OS boot, Ubuntu 12.04 installation
4. Drive is a Samsung SSD 840 Pro. Though tried different drives also, including 2 other SSD (kingston) and a old-school Seagate Barracuda HD 7200 rpm.

I assume it's UEFI here that's tripping me up, as I have done this successively several times in the past, without UEFI MB.

I looked in the BIOS, and there was nothing obvious on changing UEFI to a legacy BIOS.
The BIOS (rather UEFI) recognizes Ubuntu as an OS on the SSD, and I have it selected as the 1st boot device. It does also recognize the SSD as a raw device and gives me that option as a boot device also. Tried that too, to no avail.
 
Odd thing to add, is I did get it the orig PC to clone ONCE, but not really sure how I did it. (persistence was about the only thing worth noting) Can not get it to clone again to a 3rd PC. These computers are for public use in a Public Library, and I need to clone this original PC 9 or 10 times.

Should I be using a different cloning program other than Clonezilla to deal with the UEFI? On their web page it states that they included UEFI support several versions ago. 
I need to keep 12.04 as it is the LTS. (the orig PC has been updated to latest Ubuntu patches)

Any ideas?
Could I create a "backup" of everything on PC, install a fresh copy of Ubuntu on a new PC, then RESTORE my backup to bring EVERYTHING over to the fresh install? (I have many, many tweaks and additions for security, printing, accessing file server etc on orig PC)

Thanks

---

### Post by VMC on 2013-10-10
If you cloned the drive using a legacy bios, then clonezilla backed up legacy mbr and not for uefi.
I don't have uefi, but there are lots of info on fixing uefi booting.
edit: Maybe [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") would get your eufi restored. Also this [UEFI]("https://help.ubuntu.com/community/UEFI") help source.

You can setup your BIOS either legacy or UEFI. Look into your BIOS for options regarding booting/mbr.

---

