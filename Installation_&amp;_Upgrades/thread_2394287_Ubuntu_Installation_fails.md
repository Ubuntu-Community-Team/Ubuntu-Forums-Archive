---
title: "Ubuntu Installation fails"
date: 2018-06-15
forum: Installation &amp; Upgrades
---

### Post by arda51616 on 2018-06-15
Hello 

bought a new ideapad 320 and tried installing ubuntu few times yet everytime it stops at installing grub2 package. Have gone over and over again to format my 1 tb disk again but it always stops halfways. I also tried to try before installing and running the boot repair. Is there another version of ubuntu that doesnt result in this or is this common? What would recommend me to do?

---

### Post by ubfan1 on 2018-06-15
Do you have an EFI partition (300M FAT filesystem)?  A UEFI install needs a place to put the grub bootloaders, and that's where they go.  Without it, grub install will fail.  Possibly, an existing EFI is too small (Windows usually has one big enough to fit grub), or the EFI had a filesystem problem.

---

### Post by oldfred on 2018-06-16
You also have to be sure to boot installer in boot mode, that you want to install. UEFI offers two boot modes from UEFI boot menu to boot USB flash drive. UEFI and BIOS/CSM/Legacy.
And then once installed you have to have system set to boot in that same boot mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Post this from live installer:
sudo parted -l

See also link below in my signature.

---

