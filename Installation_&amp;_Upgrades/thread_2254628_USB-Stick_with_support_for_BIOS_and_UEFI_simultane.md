---
title: "USB-Stick with support for BIOS and UEFI simultaneously"
date: 2014-11-28
forum: Installation &amp; Upgrades
---

### Post by BIOSaUEFIatsTime on 2014-11-28
Hi,

I'm attempting to install Ubuntu with support for BIOS and UEFI.

Tool: Unetbootin
BIOS: Syslinux 4.04 (works)
UEFI: Grub 2 (broken)

> /usr/sbin/grub-probe: error: failed to get canonical path of /cow.

Does Grub support BIOS and UEFI simultaneously? So i don't need Syslinux anymore?
How can I update grub?

Regards,
BIOSaUEFIatsTime

---

### Post by oldfred on 2014-11-28
Since the installer is on a FAT32 partition with the boot flag, it can be seen from BIOS and boot with syslinux and the rest of syslinux BIOS boot code. Or it can be seen as a efi boot partition and boot from the efi files using grub.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Each type of install may need different boot parameters to boot. Or the video may work in one mode but need help with nomodeset boot parameter in the other mode.

If you want a full install on a flash drive it takes a bit of effort to install both grub-pc(BIOS) and grub-efi-amd64(UEFI) as normally one is uninstalled when the other is installed. Drive must be gpt partitioned and have both efi partition and bios_grub partition.

      
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by sudodus on 2014-11-29
> **BIOSaUEFIatsTime said:**
> Hi,

I'm attempting to install Ubuntu with support for BIOS and UEFI.

Tool: Unetbootin
BIOS: Syslinux 4.04 (works)
UEFI: Grub 2 (broken)



Does Grub support BIOS and UEFI simultaneously? So i don't need Syslinux anymore?
How can I update grub?

Regards,
BIOSaUEFIatsTime

Welcome to the Ubuntu Forums :-)

Do you want to make a USB live drive (in a pendrive or external hard disk drive), a persistent live drive, or an installed system? You can make a USB live drive from an Ubuntu flavour desktop 64-bit iso file

- a live drive using [mkusb]("https://help.ubuntu.com/community/mkusb") - easy

- a persistent live drive using the [Startup Disk Creator]("https://help.ubuntu.com/community/Installation/FromUSBStick#Install_and_run_Startup_Disk_Creator_alias_usb-creator") alias usb-creator-gtk. There are bugs but it is possible to avoid them and succeed - more difficult

- an installed system according to [this link]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS"). But I have found that upgrading the kernel can break the dual BIOS/UEFI feature - most difficult

[https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by BIOSaUEFIatsTime on 2014-11-29
I already know these tutorials.

After upgrading the kernel, booting to UEFI Mode isn't possible anymore.
I can't update grub due to an error.
> 
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

---

### Post by sudodus on 2014-11-29
Referring to upgrading and /cow, I think you are talking about a persistent live system. Is that correct?

It does not work to upgrade the kernel of persistent live systems. You can upgrade other packages, but not the kernel. This is a limitation of persistent live systems, that you cannot get around (at least I don't know how to do it).

---

### Post by BIOSaUEFIatsTime on 2014-11-29
Yes, I use a persistent live system.

Upgrading the kernel works quite well, only UEFI Mode isn't possible anymore.
Legacy is unaffected and continues to work.

---

### Post by sudodus on 2014-11-29
It is [good] news to me that upgrading the kernel works quite well for a persistent live system in BIOS mode :-)

Maybe you get similar problems as I do with the installed system, when upgrading the kernel in a system, that is supposed to work in both BIOS and UEFI mode. If you don't know exactly what to look for (manually), I suggest that you try with [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") according to the sequences in this link

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Detailed_instructions-1](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Detailed_instructions-1)

---

### Post by BIOSaUEFIatsTime on 2014-11-29
How can i gain write access to /cdrom in order to update grub?

---

### Post by sudodus on 2014-11-29
If it is a FAT32 file system on a USB pendrive (typical for the Unetbootin case), I think it should be possible to mount that partition with read/write access, maybe even from the same system, but at least if booted from another drive. I have a memory of using that partition for saving data files (from inside the system), but I'm not 100% sure, because it was years ago.

If it is important to update/dist-upgrade including the kernel, maybe it would be easier for you to use an installed system according to my wiki page. Otherwise, I suggest that you simply avoid upgrading the kernel, and then the persistent live system should work well.

---

### Post by BIOSaUEFIatsTime on 2014-11-29
/cdrom is already mounted as read only. 
How can I gain write access?

---

### Post by sudodus on 2014-11-29
If you boot from another drive it should work to mount it read/write.

---

