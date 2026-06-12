---
title: "Grub not working after installation on ssd [Closed]"
date: 2017-07-26
forum: Installation &amp; Upgrades
---

### Post by DeinosG on 2017-07-26
Hi,
I bought a PATA SSD for an old HP/Compaq Laptop.
I tried  to install Lubuntu 16.04, and also Ubuntu Mate 16.04 (both from USB and DVD). 
After installation procedure completed I rebooted, but  received an error from GRUB saying something like "Trying to read or write outside disk 1" and the prompt of grub.

I installed Win7 from a DVD and everything went OK, at the end of installing procedure I was able to reboot and log on in Windows, so I think the SSD is Ok.

I searched on forums around, but I found no explanation of the error.

Here is what I tried as disk geometry:
- leave a small partition/empty space before root partition
- make a separate boot partition and put bootloader on MBR
- make a separate boot partition and put bootloader on it

I always receive same error.

Any help would be very appreciated.

Thank in advance
Dino

---

### Post by yancek on 2017-07-26
A default windows 7 install is going to be an MBR install so install Ubuntu and let it have the defaults for installing the bootloader.  It should install some boot code to the MBR and other boot files will be on the system partition.  You don' t need a separate boot partition as it just complicates matters.  If you used a small space/partition before the system partition, that sounds like GPT.  If you have GPT with Ubuntu you can install either UEFI or MBR but you cannot have windows on a GPT partitioned disk unless you are using UEFI.  Do you have an EFI partition and did you install windows 7 EFI?

---

### Post by oldfred on 2017-07-26
Do you have AHCI on in BIOS? Not RAID nor IDE?
You may have to add AHCI drivers to Windows first for it to work with AHCI on.
Very old systems may not even have that setting, but it is required for trim to work on SSDs.

Old IDE systems had a limit on booting from first 136GB of a drive. Or all grub/kernel files have to be inside the limit.

---

### Post by DeinosG on 2017-07-28
Thank you yancek for the replay.
No I don't have UEFI and GPT as the laptop is very old. I tried to leave a small space before the system partition because I read this adivice somewhere on the Internet.
Also I used a separate boot partition following some schemas I found googling.

I managed to install Ubuntu and other Linuxes lots of times before, both on MBR and UEFI, but I never found such an error ("trying do read/write outside disk1").
I suppose it is a Grub error.
I will reinstall Win7, even if I don't use it, and will try a dual-boot with Lubuntu.

Thank you again.

Dino

---

### Post by DeinosG on 2017-07-28
Thank you oldfred for your reply.

The laptop is very old (12 years) and the BIOS settings are very poor.
I did'n find AHCI setting.
The drive is a small 64 GB pata ssd, and Lubuntu is the only system, so boot is from first "sector".

As I wrote before, I will install Win7 again, just to "revive" MBR and then I will install Lubuntu in dual-boot.

Thank you again 
Dino

---

### Post by DeinosG on 2017-08-20
After various attempts, I almost am sure the drive is defective.
It is a very weird thing, because I was able to install Win7 but no flavour of Linux with grub2.
Any attempt to repair grub2, or reinstall it gave no result. 
So I decided to return it to Amazon.

Thanks to everyone

---

