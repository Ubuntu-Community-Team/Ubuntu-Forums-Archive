---
title: "remove efi from ubuntu"
date: 2021-07-16
forum: Installation &amp; Upgrades
---

### Post by Old Duffers on 2021-07-16
How can I remove efi from ubuntu?

---

### Post by TheFu on 2021-07-16
If your computer system doesn't use EFI, then Ubuntu won't install using it.
So, don't install Ubuntu with EFI enabled.  That's a BIOS setting in the motherboard firmware, not an OS setting.

---

### Post by yancek on 2021-07-16
A little context as to why you want to do this?  If your computer is using EFI, then any operating system on it will fail to boot if you remove the EFI partition.  Do you have multiple EFI partitions on the same drive?  Do you want to delete an EFI partition on aa secondary drive?

---

### Post by grahammechanical on 2021-07-17
A GUID Partition Table (GPT) hard drive in a BIOS motherboard will have a small system boot partition that is described as EFI System. I know this is true because it is what I have in my machine. GPT is preferable to MBR even with BIOS motherboards.

On my system it is only 52 MB. It is not getting in the way of anything. I do not think that much would be gained by deleting it.

Regards

---

