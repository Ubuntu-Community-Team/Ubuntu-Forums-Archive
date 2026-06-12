---
title: "Instaling Ubuntu on a pre-installed Win8 machine"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by Vormeph on 2013-08-20
I got a new laptop which had Windows 8 pre-installed (yuck!) and am determined to completely erase Windows 8 and install Ubuntu over the entire hard drive instead. I disabled Secure Boot and enabled Legacy BIOS. Do I still have to keep the EFI partition? Do I need to perform any other modifications to my laptop before installing Ubuntu?

---

### Post by erasmusp on 2013-08-20
I am sure somebody will respond on the EUFI question but I was just wondering: Being a new laptop did you boot from the live CD first and made sure everything is working, like sound, track pad, WiFi, LAN, screen resolution, etc?

---

### Post by Vormeph on 2013-08-20
> **erasmusp said:**
> I am sure somebody will respond on the EUFI question but I was just wondering: Being a new laptop did you boot from the live CD first and made sure everything is working, like sound, track pad, WiFi, LAN, screen resolution, etc?

Last I checked everything seemed to work flawlessly. 

I just need to know if I am required to keep the EFI partition or not.

---

### Post by Vladlenin5000 on 2013-08-20
If you intend to install Ubuntu only - good choice - then no, you aren't required to keep the EFI partition.

---

### Post by oldfred on 2013-08-20
If depends on whether you want UEFI boot, or BIOS boot, or maybe later may want UEFI boot. It is hard to add an efi partition to the beginning of a drive after you have filled with data. But if booting with CSM/BIOS/Legacy you do not need the efi partition.

If drive is still gpt partitioned (required if UEFI boot) you can boot Ubuntu in BIOS mode but then need a 1MB unformatted partition with the bios_grub flag.

If you convert drive to MBR(msdos) you will not be able to boot with UEFI and are back to the MBR 4 primary partition limit, extended partitions and logical partitions.

---

### Post by Vormeph on 2013-08-21
I'm not really that convinced with UEFI, and prefer the old system because it works for me. In which case I'll boot Ubuntu without an EFI partition; with legacy boot enabled; with all other UEFI-related features disabled.

---

