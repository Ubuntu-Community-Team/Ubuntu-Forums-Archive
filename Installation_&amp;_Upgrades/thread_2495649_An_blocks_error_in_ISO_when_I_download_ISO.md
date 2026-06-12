---
title: "An blocks error in ISO when I download ISO"
date: 2024-02-26
forum: Installation &amp; Upgrades
---

### Post by tommynights on 2024-02-26
This is the story!
 I have two disks
 A 500gb SSD drive with windows on it
 Another 64 GB disk where I installed Ubuntu
 I have a Lenovo IdeaPad 1-11IGL05 Laptop
 The installation went well
 Where it goes wrong is when booting GRUB to be able to choose between the 2 OS
 but when I turn on the computer I'm in a reboot loop with a brief glimpse of "reset system"
 I press F12 and I have the boot menu but when I choose Ubuntu instead of Windows it starts Windows for me in all cases!  Ubuntu # the name speaks for itself 

 eMMC Card: SanDisk 64GB # where Ubuntu and its EFI system are located

 Grub2Win EFI - 64bit # I had installed Grub2Win to help me resolve GRUB from Windows but it accidentally deleted and replaced the Windows boot manager

 NVMe: Lexar 500GB SSD # where Windows is and its EFI.  

I checked the Ubuntu ISO with windows and it detected 8 corrupt blocks!
 Block 681 to 687

---

### Post by ajgreeny on 2024-02-26
It is worth running the Boot-info  script from Boot-Repair (see my signature below for a **how-to** using the live OS you used to install Ubuntu and from that script show us the **pastebin** URL that you will be given in the output.
Do not copy and post all the output, just that link.

From what you have said so far it is difficult to diagnose the problem and that output should give us a lot more detail.

---

### Post by tea for one on 2024-02-26
> **tommynights said:**
>  A 500gb SSD drive with windows on it
 Another 64 GB disk where I installed Ubuntu
 I have a Lenovo IdeaPad 1-11IGL05 Laptop
 The installation went well
Are these both internal disks?
 > **tommynights said:**
> Where it goes wrong is when booting GRUB to be able to choose between the 2 OS
 but when I turn on the computer I'm in a reboot loop with a brief glimpse of "reset system"
 I press F12 and I have the boot menu but when I choose Ubuntu instead of Windows it starts Windows for me in all cases!  Ubuntu # the name speaks for itself 
Access your UEFI settings with dedicated key F2
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 

Disable the following (if present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock
> **tommynights said:**
> Grub2Win EFI - 64bit 
I have no idea what this does.
> **tommynights said:**
> I checked the Ubuntu ISO with windows and it detected 8 corrupt blocks!
Block 681 to 687Double check the Ubuntu ISO with sha256sum

---

