---
title: "No boot loader, Operating system found"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by stacs2 on 2016-02-25
Need some serious help, I tried installing arch but couldn't get installed.

 Now I'm just trying to get ubuntu back as i really need this laptop for school but after the installation after reboot I get: 
No boot device found
Please install an operating system on your hard disk
Hard disk (3F0)

When i "try ubuntu from the usb stick" again my wifi settings and web page is still loaded from previously trying to re-install ubuntu... When re-installing and erasing disk it says to reboot and when i pull the usb it shows no boot device found, please install an operating system.

Tried boot-repair from ubuntu on the usb it says "The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition(FAT32, 100MB~250MB, start of the disk,boot flag).

[http://paste.ubuntu.com/15196399/](http://paste.ubuntu.com/15196399/)

Laptop is hp envy m6 preinstalled with windows 8, that I had erased and installed ubuntu as main my main OS.

---

### Post by grahammechanical on 2016-02-25
> preinstalled with windows 8, that I had erased and installed ubuntu as main my main OS.

How did you erase Windows 8? Did you do it when you installed Ubuntu by selecting the Erase disk & install Ubuntu option? Were you dual booting Ubuntu & Windows 8 and then did you erase Windows 8?

When Windows 8 (and later) comes pre-installed then Windows 8 is installed in EFI mode & Ubuntu must also be installed in EFI mode. The installation process of Windows 8 would have created an efi boot partition into which the Windows 8 efi boot files are put. When we dual boot with a pre-installed Windows 8 & later the Ubuntu installer places Ubuntu efi boot files in the efi boot partition used by Windows.

If we then delete the Windows 8 partitions including the efi boot partition we will likely get this situation where Ubuntu has been installed in EFI mode but the efi boot partition is missing.

Boot Repair cannot create an efi boot partition. When you re-install Ubuntu are you running the live session in EFI mode or BIOS/Legacy mode? If you run the live session in EFI mode the installer should create an efi boot partition as part of the boot process.

You may also need to look into the UEFI boot system utility settings. It may have some references to Windows 8 that are causing some confusion.

Regards.

---

### Post by oldfred on 2016-02-25
It looks like you have installed in BIOS boot mode with MBR(msdos) partitioning.

Have you gone into UEFI and changed boot mode to BIOS/CSM/Legacy or whatever HP calls it?

---

### Post by stacs2 on 2016-02-25
> **grahammechanical said:**
> How did you erase Windows 8? Did you do it when you installed Ubuntu by selecting the Erase disk & install Ubuntu option? Were you dual booting Ubuntu & Windows 8 and then did you erase Windows 8?

When Windows 8 (and later) comes pre-installed then Windows 8 is installed in EFI mode & Ubuntu must also be installed in EFI mode. The installation process of Windows 8 would have created an efi boot partition into which the Windows 8 efi boot files are put. When we dual boot with a pre-installed Windows 8 & later the Ubuntu installer places Ubuntu efi boot files in the efi boot partition used by Windows.

If we then delete the Windows 8 partitions including the efi boot partition we will likely get this situation where Ubuntu has been installed in EFI mode but the efi boot partition is missing.

Boot Repair cannot create an efi boot partition. When you re-install Ubuntu are you running the live session in EFI mode or BIOS/Legacy mode? If you run the live session in EFI mode the installer should create an efi boot partition as part of the boot process.

You may also need to look into the UEFI boot system utility settings. It may have some references to Windows 8 that are causing some confusion.

Regards.



I originally had my laptop dual booted with windows 10 (upgraded from windows 8) and ubuntu.  Then I ended up completely installing ubuntu as my main OS.  It was working fine until I tried installing arch, as I've installed arch on my previous laptop but this time around I messed up somewhere.

I'm currently working off the ubuntu live usb, which seems to have saved my wifi settings and previous web pages even if I remove the usb...

---

### Post by stacs2 on 2016-02-25
> **oldfred said:**
> It looks like you have installed in BIOS boot mode with MBR(msdos) partitioning.

Have you gone into UEFI and changed boot mode to BIOS/CSM/Legacy or whatever HP calls it?

I believe this was where my mistake was then, while installing arch and doing the partition a prompt popped up askin me to choose, and I just chose msdos.....

I have not tried switching to legacy mode as it gives a warning prompt and I didn't want to mess with anymore before getting advice on here.

Should I repartion in gpt?

---

### Post by oldfred on 2016-02-25
The only way you can boot is with BIOS/Legacy.

Or else you have to change to gpt and totally re-install everything in UEFI boot mode. 

How you boot install media is how it installs, UEFI or BIOS.

---

### Post by stacs2 on 2016-02-25
> **oldfred said:**
> The only way you can boot is with BIOS/Legacy.

Or else you have to change to gpt and totally re-install everything in UEFI boot mode. 

How you boot install media is how it installs, UEFI or BIOS.

Switching to legacy mode worked!!!

I will change thread to solved, THANK YOU!

Loading my back up of ubuntu now.

Is there any harm running ubuntu in legacy mode though? I think later I will do another clean wipe and boot into UEFI mode anyway if it does make any difference

---

### Post by sudodus on 2016-02-26
No harm, you can continue running Ubuntu in legacy mode :-)

You need not change it in this computer. Maybe your next computer will only run in UEFI mode (depending on the actions of Microsoft and the manufacturer of that computer).

---

