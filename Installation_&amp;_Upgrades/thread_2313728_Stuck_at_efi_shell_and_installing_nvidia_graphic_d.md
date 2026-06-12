---
title: "Stuck at efi shell and installing nvidia graphic driver"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by Tegg_Sung on 2016-02-15
My desktop environment is MSI Z170 Krait Gaming board, Intel i7-6600 Skylake, GTX970, and would like to install Ubuntu 14.04 LTS. 

Trying to install Linux, I set BIOS information. Originally, booting mode is "legacy+UEFI". Only turning "Windows OS configuration" enable, secure boot option showed up. So I turned secure boot and fast boot option off. Then instead of "legacy+UEFI mode", just "UEFI mode" has been set. And somehow, the computer cannot recognise external graphic driver, so switched to Intel internal graphic driver.

 After putting install CD, "ACPI PCC probe failed" showed up and installing GRUB did not show up. So I manually added "nomodeset" and could found GRUB message. I installed Ubuntu step by step, removing installing CD-ROM, and rebooted. But then, instead of GRUB message, "EFI shell" kept showed up, and this is because there was no installing USB or CD is connected (I have no idea how to get into GRUB from EFI shell). So I entered BIOS setting again and turned "windows os configuration" on to turn secure boot on and rebooted. At this time, I could get into Ubuntu screen. 

The problem is that I want to use external graphic card. If I changed graphic configuration(PCI, IGP) in BIOS, then the Ubuntu cannot detect it, and only showed up to 1024x768 resolution. Then, Ubuntu is recognised another graphic card, not nVidia or Intel one. 
Following with other blogs explanations, I tried setting "nouveau" to 0 and making blacklist nouveau, and installed the newest nVidia graphic driver that is matched (All done by several steps). However, I stuck at "log-in menu". Even though I entered correct password, it kept showed same log-in screen, and could not get into Ubuntu desktop screen (The highest resolution is still 1024x768, and probably the reason is that matched graphic driver is not installed yet).

How to solve this graphic driver problem? And can GRUB booting message be showed instead of "EFI shell"? My final goal is installing Windows 10 in external HDD disk and using GRUB booting menu, two separate OS be switched individually (And that's why I have troubles in "Windows OS configuration", "secure boot", and "EFI shell" things). 
I think that MSI board and BIOS are making troubles and confusions. Could anybody give me some help?

---

### Post by tanguy3 on 2016-02-15
Hi 
I think I had the same issues (having as well a 970GTX) - it took me some time.
Have a look on this thread that just got solved : [http://ubuntuforums.org/showthread.php?t=2313319](http://ubuntuforums.org/showthread.php?t=2313319)
This could reply to lots of your questions...
Best,
Tanguy

---

### Post by oldfred on 2016-02-16
You cannot install Windows to external drive, unless possibly eSATA that is still seen as an internal drive.

Better to use UEFI, but should not be required. But if dual booting, best to have both Windows & Ubuntu in same boot mode or both BIOS or both UEFI.

Ubuntu can boot in BIOS or UEFI boot mode from gpt(GUID) partitioned drive.
Windows only boots in BIOS mode from MBR(msdos) partitioned drives.
Windows only boots from gpt partitioned drives with UEFI.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

