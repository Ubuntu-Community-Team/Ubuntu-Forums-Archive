---
title: "Dual Booting Ubuntu with Windows 8.1"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by stavgus on 2013-11-18
Hello Ubuntu Community

I have recently purchased a new SSD which i installed Windows 8.1, and now I want to dual boot Ubuntu. I currently have 2 SSDs in my computer 1 which as i Mentioned has Windows 8.1 installed, and another that I want to install Ubuntu 13.10 on.

1. If I have 2 SSDs do I still need to disable features like FastBoot and SecureBoot or is that not needed anymore?

2. Can I "UEFI-boot" Ubuntu?

3. Any more things that can cause problems for me?

4. Where will GRUB be installed? on the Win 8.1 SSD or the Ubuntu SSD?

I just want to know if there can be any conflicts with installign Ubuntu 13.10 on my setup the way i want it so I know if I need to disable things or change my configs before installing, But optimal would be if I dont need to disable any feature.

My plan is to have my Win 8.1 as my Primary OS (for now ^^), and boot into Ubuntu only when I need to.

I just want to 

PC Specs:

Motherboard: Asus P8P67-Deluxe
Processor: Intel i7 2700k
Graphics card: GTX 560 Ti
SSD1(Windows 8.1): Samsung 840 EVO 250GB
SSD2(Which I want to install Ubuntu on): Intel 510 120GB
Storage Disk: 2TB Western Digital Caviar Green
RAM: 8GB G-Skill ripjaw DDR3
PSU: Corsair AX850 

Thanks in advance, Im sorry if I have rushed the text too much, if you want me to rewrite something so you can understand better please inform me.

---

### Post by fantab on 2013-11-18
> **stavgus said:**
> 
1. If I have 2 SSDs do I still need to disable features like FastBoot and SecureBoot or is that not needed anymore?
[COLOR=#000080]*Try Installing ubuntu with Fastboot and Secureboot enabled. This should work, if it doesn't then we can disable these later.*[/COLOR]

2. Can I "UEFI-boot" Ubuntu?
[COLOR=#000080][I]Yes you can. This depends on how you've installed Windows8; if you've installed it in UEFI then install Ubuntu in EFI mode. Post the output of the following command from Ubuntu Live, [the ouput is important to guide you further]:
```
sudo parted -l
```
[/I][/COLOR]
3. Any more things that can cause problems for me?

4. Where will GRUB be installed? on the Win 8.1 SSD or the Ubuntu SSD?
[COLOR=#000080][I]By default it will install on the First SSD or HDD. If you want it somewhere else then you have to manually guide it, that is change the default setting. 
Installing Grub to SSD with Ubuntu is a very good idea.[/I][/COLOR]

My plan is to have my Win 8.1 as my Primary OS (for now ^^), and boot into Ubuntu only when I need to.
[COLOR=#000080]*This can be done via Grub, or via Bios. Through grub the process will be cleaner and simpler.*[/COLOR]


Post the output of the requested command using Ubuntu DVD/USB.

---

### Post by oldfred on 2013-11-18
It will be easier to dual boot if both systems are BIOS boot or both systems UEFI boot. 
You can have each different, but have to boot from UEFI not grub menu and may have to turn on/off BIOS/UEFI settings each time you change. UEFI & BIOS are not really compatible so once you start booting one way you cannot switch.

If new system I would suggest using gpt partitioning whether BIOS or UEFI boot. And include both an efi partition and a bios_grub partition on every drive.
Windows only boots from gpt partitioned drives with UEFI.
Both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.
But Ubuntu will boot from gpt with UEFI or BIOS and can even be converted if efi(UEFI) or bios_grub(BIOS) partition exists.

So the only time not to use gpt is if you want Windows booting in BIOS mode on the same drive.

---

