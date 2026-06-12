---
title: "install v22.04 in LEGACY mode, not UEFI - because 3F0 on HP DriveLock"
date: 2022-10-02
forum: Installation &amp; Upgrades
---

### Post by pawelnrg on 2022-10-02
The question about HP Laptops and the problems of installing 22 version appears dozens - hundreds of times, but I have not found answers, all are answers I found evasive and around. I will try to ask as simply as possible.
Fact / symptom: laptop HP8770 (and others) UEFI not work with drive lock ;( must be "legacy".....   The requirements are complicated because there is drive lock a and  encryption of the installation, on the old version Ubuntu it was  possible. (I know, strange for my is OK.  And everyone got used to it). We choose for ourselves from the BIOS from which disk to boot the system. do not need GRUB, etc.

Q: how force legacy when install new Ubuntu? 

Q: Is the inability to install in "legacy" considered a bug? - this is a question for the developers. but I do not know where to ask it so it is here. please pass it to development, or wherever should be asked.

---

### Post by TheFu on 2022-10-03
If you want a legacy boot install, don't enable UEFI.  Disable it in the BIOS.  If that isn't possible, there isn't any method that I know.  Some vendors don't allow BIOS settings to be accessed.  The only real solution for that is to stop buying their computers. Vote with your money. Take your business elsewhere.

I can assure you that 22.04 installs without UEFI.  I have 2 Legacy installations running now.  The bug is with HP and other vendors who mandated UEFI as required.  There's a difference between optional and mandated.  UEFI is definitely optional on Ubuntu.

BTW, the Linux Foundation recommends using UEFI and secure boot in their workstation security best practices since 2015. [https://www.computerworld.com/article/2977885/linux-foundations-security-checklist-can-help-harden-workstations.html](https://www.computerworld.com/article/2977885/linux-foundations-security-checklist-can-help-harden-workstations.html)
A direct link to their checklist: [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md)

Yes, that github link is from the Linux Foundation: [https://github.com/lfit](https://github.com/lfit)

---

