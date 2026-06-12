---
title: "dual boot ubuntu with windows 8 pre-installed"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by imraan196 on 2013-03-24
[http://paste.ubuntu.com/5644829/](http://paste.ubuntu.com/5644829/)

Hi 

I  have a lenovo k430 with pre installed windows and I installed ubuntu  12.10 64-bit on UFEI however the grub menu does not show and windows is  booted.

I tried using boot repair recommend twice however this did not work 

Any advice will be much appreciated 

Thank you

---

### Post by oldfred on 2013-03-24
You have to go into the UEFI menu and choose to boot ubuntu.

Did you install Ubuntu in BIOS/Legacy/CSM mode or UEFI mode. Since you have grub in the MBR, it looks like you did.
Some have to install in BIOS mode and then use Boot-Repair to convert to UEFI. 

       You also have Refind which I know almost nothing about, it looks like it was from Mint?
Not all Distributions support secure boot yet.

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

