---
title: "No option to dual boot Ubuntu with Windows"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by e-uduntu-g on 2014-10-26
Hello,

I have downloaded Ubuntu 14.04.1 and burned it to DVD and it boots fine from that DVD. When I choose install, it does not give me the option of dual booting, only to install over windows.

Computer is an HP pavilion laptop

J

---

### Post by e-uduntu-g on 2014-10-26
a bit more info,

If I boot in standard CD mode, the problem is as described with only the option to over write.

If I boot in UEFI CD mode, then the only install option is 'no OS installed, format drive and install'

J

---

### Post by oldfred on 2014-10-26
What version of Windows and/or UEFI or BIOS Windows install?

Best to use Windows own disk tools to shrink the NTFS partitions. 
If Windows 7 with BIOS you probably have all 4 primary partitions used with MBR(msdos) partitioning.
If Windows 8 with UEFI you need to make sure fast boot or always on hibernation is off and usually better to have secure boot off.

HP are not Linux friendly, and need work arounds to boot Ubuntu if UEFI based.

Post this from Ubuntu's terminal.
sudo parted -l

That will show if gpt and then it must be UEFI as Windows only boots UEFI from gpt drives. 
Or it will show all 4 primary partitions if BIOS and MBR.

---

