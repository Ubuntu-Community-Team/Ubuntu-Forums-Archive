---
title: "big trouble installing ubuntu 12.4 and uefi"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by edo vulcano on 2013-04-16
i've got an asus laptop with uefi
i'm trying to reinstall ubuntu 12.4 via usb, but the procedure stops after the grub screen.
if i choose (install ubuntu) the screen turn to black and pc stops.
how can i solve this problem?

---

### Post by ajgreeny on 2013-04-16
Dual boot or single OS of Ubuntu?

Either way, you must make sure that secure boot is disabled, and you must boot the USB in UEFI mode if you wish to install in that mode.  However, you are talking about the grub screen, so have you already installed Ubuntu and are now unable to boot successfully to it, or do you mean the boot screen that you may see when running the USB?

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for more details of the procedures needed.

---

### Post by edo vulcano on 2013-04-16
i want just  an os! (12.04)
at the moment i'm running ubuntu 12.10
in the bios i can't see anything about secure boot; i can just  setup uefi (on/off).
when i reboot from usb (uefi sandisk) i can see the grub menu but,i cant' proceed,coz if i choose install ubuntu ,i see a black screen and nothing else

---

### Post by oldfred on 2013-04-16
What video?
At grub menu you probably need nomodeset and/or maybe that plus other boot parameters.

Press e to edit grub boot stanza (one time edit) and replace splash quiet with nomodeset. With UEFI you do not get the BIOS type startup, but more like the grub menu at first boot.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Was this a Windows 8 pre-installed system? If so you do have secure boot. If it was Windows 7 then you do not have secure boot. But probably should make sure you have the newest UEFI/BIOS from your vendor. Vendors are making lots of fixes & updates to UEFI as well as Ubuntu (and Windows) fixing how to work with UEFI.

Still best to use the newer 64 bit versions of Ubuntu as that has the newest updates for UEFI.
      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI.

---

