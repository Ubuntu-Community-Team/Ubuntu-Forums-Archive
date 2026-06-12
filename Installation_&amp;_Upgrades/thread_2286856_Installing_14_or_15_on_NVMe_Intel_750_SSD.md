---
title: "Installing 14 or 15 on NVMe Intel 750 SSD"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by anton35 on 2015-07-15
The SSD is recognized, partitioned, installation files are written. But it fails while trying to install GRUB into MBR. Are there any guides that help to deal with VNMe SSDs?

---

### Post by Bucky Ball on 2015-07-15
Welcome. I'm thinking this might have to do with the way you are installing it. Are you installing in EFI or legacy mode? Have you got secureboot disabled in the BIOS? Try that.

---

### Post by oldfred on 2015-07-15
Supposedly fixed a year ago for NVMe devices.
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746396](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746396)

So is issue really something else? Are you using gpt but do not have either an efi parition for UEFI boot or a bios_grub partition for BIOS boot?

Post this:
sudo parted -l

---

### Post by anton35 on 2015-07-15
Managed to install Ubuntu 15 in UEFI mode by tweaking some BIOS settings. In UEFI mode there was no problem installing GRUB into MBR.

Thanks for the tips!

---

