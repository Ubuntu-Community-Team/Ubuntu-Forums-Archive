---
title: "dual boot Win8 &amp; 12.04.2 - always boots to Win8 without LiveUSB"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by Tha_Libster on 2013-05-16
I'm trying to create a dual boot of Windows 8 and Ubuntu 12.04.2 on my ASUS N56VJ notebook. I followed [this]("https://help.ubuntu.com/community/UEFI") guide to the letter. The Boot-Repair "Recommended repair" seems to run fine, and doesn't give me an error or troubleshooting URL (which the guide mentioned it might), but when I reboot without the LiveUSB, the computer just boots to Win8.

My BIOS doesn't make it extremely clear whether the HDD is booted in EFI or legacy, but from the guide, running the command:

    [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 


returns a result of **legacy**. What I'm confused about is that it mentions later in the same guide that the **same command** is used to determine whether **Ubuntu** is installed in EFI or legacy. My understanding is that they should be either both in EFI or both in legacy, but shouldn't they technically be independent?

Anyway, I tried [both sections in the guide]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode") for converting Ubuntu to EFI and converting Ubuntu to legacy, which is essentially just selecting or deselecting **Separate /boot/efi partition** in the **Advanced options -> GRUB location **submenu of boot-repair. It also requires setting up partitions, which I think I have done correctly; [here]("http://i.imgur.com/6pL06xR.png")'s what my gparted looks like in case I'm mistaken.

I guess what I want is for GRUB to appear when I boot. But I'm pretty new to this, so I have no idea what is missing at this point.

Thanks in advance for the help.

---

### Post by oldfred on 2013-05-16
The bios_grub partition is only used by grub2 when it installs a boot loader to the protective MBR of a gpt drive to boot in BIOS mode. That is how I boot as my system is not UEFI.

If you used Boot-Repair to convert to UEFI then the bios_grub would not be used anymore and you would be booting in UEFI mode from efi partition. There are two (really 3) versions of grub. For BIOS you have grub-pc, for UEFI you have grub-efi. But grub-efi also has a signed version with signed kernels for those systems that only boot with secure boot on. If booted with UEFI in secure boot mode you can have Boot-Repair update grub to the signed versions.
Also some systems only boot the Windows efi file. For those Boot-Repair backsup & renames files.

While you can dual boot by going into UEFI/BIOS and turning on CSM/BIOS/LEgacy mode to boot Ubuntu in BIOS mode and then go back to UEFI/BIOS and change to boot in UEFI mode (maybe with secure boot on) to boot Windows, that can be a real hassle. Better if both are installed in UEFI mode.

 Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

Those with Asus K55n can get Ubuntu to work in BIOS mode, but video never works in UEFI mode. Not sure if issue with your model or not. It seems like a UEFI issue the vendor has to resolve.

Post link to BootInfo report from Boot-Repair.

---

### Post by Tha_Libster on 2013-05-16
Here's the report: [http://paste.ubuntu.com/5669773/](http://paste.ubuntu.com/5669773/)

I checked out the instructions in the thread you linked and it seems that I've followed them all. Maybe it has to do with the fact that the author was installing 12.10? Like I said, I'm not sure if my HDD is set to boot in EFI or legacy, because there doesn't seem to be a clear indicator as in the examples in the guide. All I know is that running the aforementioned command seems to indicate it boots in legacy.

Thanks for the quick response.

---

### Post by Tha_Libster on 2013-05-16
Not sure what the policy is here with bumping threads, but I still haven't been able to figure out how to get the bootloader to appear at boot.

---

### Post by oldfred on 2013-05-16
You have the unsigned efi files with grub2 and the efi partition is commented out in fstab. So you are not using the efi files to boot, but the MBR.

You have settings in UEFI. Every vendor varies. Most have a secure boot on or off switch. Some combine switches where UEFI on means secure boot off, or BIOS/CSM on means no efi. And others have combination of efi or BIOS which just may only boot by looking at files in MBR or efi partition.

Some more UEFI screens.

---

### Post by Tha_Libster on 2013-05-16
Okay, I seem to have gotten things in working order. The setting in my BIOS I had to change was to disable CSM, which (I hadn't realized) is the equivalent of enabling EFI. I then did a reinstall of Ubuntu and boot-repair, and now I can boot successfully to both Win8 and Ubuntu through Grub.

Thanks for all the help oldfred.

---

### Post by oldfred on 2013-05-16
Glad you got it working. :)

---

