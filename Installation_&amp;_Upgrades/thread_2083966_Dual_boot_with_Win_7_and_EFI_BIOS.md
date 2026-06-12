---
title: "Dual boot with Win 7 and EFI BIOS"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by ThePinkWitch on 2012-11-14
Hi, I just had my computer totally upgraded except for the HD and I'm wondering If I will have problems with Ubuntu and Win 7 Dual boot on my system. I haven't used Linux quite a while as I had huge issues in the past with EFI BIOS, AHCI  etc running on Win XP/Ubuntu after I had a new MB. I am installing Win 7 now and that has the ACHI drivers so I'm hoping it will all go OK. I don't have any help as no one I know has any Linux experience so It needs to be fairly straight forward for me to get it working. Would love to use Ubuntu again. Thanks for any help. 
 
My system is

MB Z77MX-D3H LGA 1155 (Dual UEFI BIOS)
CPU Intel i5 2500K
Radeon HD 6870 
4G RAM 1333
PSU Seasonic S12 II Bronze 520W
Win 7 (Install 32bit or 64 bit windows?)

---

### Post by darkod on 2012-11-14
Since you are doing the win7 install yourself you should have the option in bios to disable UEFI boot and you can use the old legacy boot. Most boards have the disable option.

If you prefer using uefi, from what has been said here (I don't use uefi myself and don't plan to), the most important thing is to boot the ubuntu cd/usb also in uefi mode, so that the installation will be in uefi mode. And I think only the 64bit version is uefi compatible.

For the dvd-drive and the bootable usb stick, you will have two different boot devices, the legacy type and uefi type. You need to select to boot from the uefi type if you plan to install ubuntu in uefi mode.

Otherwise it will install it in legacy mode, and when win7 is in uefi mode the dual boot definitely won't work.

---

### Post by albandy on 2012-11-14
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by ThePinkWitch on 2012-11-14
> **darkod said:**
> Since you are doing the win7 install yourself you should have the option in bios to disable UEFI boot and you can use the old legacy boot. Most boards have the disable option.

If you prefer using uefi, from what has been said here (I don't use uefi myself and don't plan to), the most important thing is to boot the ubuntu cd/usb also in uefi mode, so that the installation will be in uefi mode. And I think only the 64bit version is uefi compatible.

For the dvd-drive and the bootable usb stick, you will have two different boot devices, the legacy type and uefi type. You need to select to boot from the uefi type if you plan to install ubuntu in uefi mode.

Otherwise it will install it in legacy mode, and when win7 is in uefi mode the dual boot definitely won't work.

Thanks for the reply. I would prefer not to use EFI mode if possible. I wasn't sure If I could install Win 7 and just have the old BIOS. EFI seems like a nightmare to me as far as Dual boot with Linux. Thanks again :)

---

### Post by ThePinkWitch on 2012-11-14
> **albandy said:**
> [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Thankyou :)

---

### Post by darkod on 2012-11-14
> **ThePinkWitch said:**
> Thanks for the reply. I would prefer not to use EFI mode if possible. I wasn't sure If I could install Win 7 and just have the old BIOS. EFI seems like a nightmare to me as far as Dual boot with Linux. Thanks again :)

If the board allows you to disable uefi boot, win7 will work just fine in legacy. Just make sure you leave the sata port mode to AHCI, that's better than IDE.

With win7 the thing is that it needs gpt partition table to work with uefi, or msdos in legacy mode. But the installer will create the necessary partition table if needed. In any case, if the win7 installer gets too confused, you can always create new blank msdos table using Gparted from the ubuntu live cd. And then continue the win7 install.

---

### Post by ThePinkWitch on 2012-11-15
> **darkod said:**
> If the board allows you to disable uefi boot, win7 will work just fine in legacy. Just make sure you leave the sata port mode to AHCI, that's better than IDE.

With win7 the thing is that it needs gpt partition table to work with uefi, or msdos in legacy mode. But the installer will create the necessary partition table if needed. In any case, if the win7 installer gets too confused, you can always create new blank msdos table using Gparted from the ubuntu live cd. And then continue the win7 install.

 So if I can disable EFI and install in legacy mode, I need to make gpt partition for Win 7 or both Win 7 and Ubuntu? This is so harder than just installing Win XP and Ubuntu on an old machine with normal BIOS :( I never had any problems before I got the new board. 
Thankyou for your help.

---

### Post by darkod on 2012-11-15
No, gpt is for using uefi. If you use legacy bios boot it's the standard msdos partition table.

As for ubuntu, it can work on both msdos or gpt regardless of uefi or not. It's windows that has the limitations.

So, for non-UEFI dual boot, you need msdos table on the hdd.

---

