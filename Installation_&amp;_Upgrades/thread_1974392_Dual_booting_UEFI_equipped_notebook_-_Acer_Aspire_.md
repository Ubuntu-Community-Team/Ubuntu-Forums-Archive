---
title: "Dual booting UEFI equipped notebook - Acer Aspire 5560"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by immerohnegott on 2012-05-06
NOTE: This only applies to systems with Windows NOT running in EFI mode, which I would wager is most of them, as running in EFI mode seems to result in unstable boot behavior, at least on some platforms.

I've spent a rough couple days getting this system up and running, and in my forum searches I spotted a couple other people having issues with this, so I thought I'd put in my two cents on the matter.

Basically, the issue I first ran into that started my rapid descent into madness was that when installing Ubuntu alongside the pre-installed Windows 7, GRUB wouldn't show up and Windows was the only OS that could boot. 

After much trial and error, and nearly kicking the computer out the m-f-ing window, I deduced that the Ubuntu installer was running in UEFI mode, and installing GRUB so that it would boot that way. The problem there is that the disk needs to be set up correctly with an EFI boot partition and a GUID partition table - neither of which were in place, as the pre-installed Windows was running in BIOS emulation from an MBR partition table.

The simple solution was to force Ubuntu to install in BIOS emulation (no switches in my system setup to force it) by renaming the "efi" directory at the root of my Ubuntu LiveUSB stick. This allows you to install GRUB to the master boot record the way God intended and let it coexist with the existing MBR-partitioned Windows install, just like any regular dual-boot setup. 

You'll know if the Ubuntu installer is loading in BIOS emulation if you get the normal purple screen with the accessibility and keyboard icons at the bottom. In UEFI mode, it just loads a black and white GRUB menu.


It IS possible to get a working dual-boot in UEFI, but at least on this system, it results in the machine freezing every other boot and at shutdown. From what I've found Googling around for fixes, there are a number of other systems that exhibit similar instabilities when booting in UEFI mode. 

</rant>
Hope someone benefits.

---

### Post by lapcat66 on 2012-09-01
Yes, that helped quite a bit.  Thank you.

I couldn't figure out how dual booting, something that's been going right for years (even with EFI computers), suddenly went so wrong.

You diagnosed the problem exactly for a Lenovo G580.  It has a UEFI setup for Windows 8, but has Windows 7 installed, and isn't actually using UEFI mode.  

The Linux installer is clever enough to see the UEFI setup, but not that the setup is not being used.  Simply renaming the efi folder on the live USB hides it from the installer, and forces a working install.

Brilliant!

---

### Post by Wim Sturkenboom on 2012-09-02
First, I like to thank you for this thread. I was wondering where my grub was gone to.

Second, my experience in the hope it helps others.

> 
The simple solution was to force Ubuntu to install in BIOS emulation (no switches in my system setup to force it) by renaming the "efi" directory at the root of my Ubuntu LiveUSB stick. This allows you to install GRUB to the master boot record the way God intended and let it coexist with the existing MBR-partitioned Windows install, just like any regular dual-boot setup.

On an Asrock H61M-VS one does not have to remove/rename the 'efi' directory. The uefi boot menu shows two entries for my memory stick (USB and EUFI); simply selecting the correct one (USB) does the trick.
> 
You'll know if the Ubuntu installer is loading in BIOS emulation if you get the normal purple screen with the accessibility and keyboard icons at the bottom. In UEFI mode, it just loads a black and white GRUB menu.

This did put me on the right track; I accidentally had used both during the 'try ubuntu' so I knew what you were talking about.

---

### Post by citro87 on 2012-09-03
Thanks a lot, that really helped!

---

### Post by YannBuntu on 2012-09-12
Hello

> **immerohnegott said:**
> when installing Ubuntu alongside the pre-installed Windows 7, GRUB wouldn't show up and Windows was the only OS that could boot. 

This is generally due to Ubuntu installed in Legacy mode when Windows is installed in EFI mode (or the contrary). In this case, solution is to convert Ubuntu into the same mode as Windows. See [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

> You'll know if the Ubuntu installer is loading in BIOS emulation if you get the normal purple screen with the accessibility and keyboard icons at the bottom. In UEFI mode, it just loads a black and white GRUB menu. 

+1
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_CD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_CD_in_EFI_mode)

---

### Post by Ragnia1980 on 2012-09-22
if i was to rename my efi folder on my usb what would i rename it to?

---

### Post by Wim Sturkenboom on 2012-09-23
> **Ragnia1980 said:**
> if i was to rename my efi folder on my usb what would i rename it to?
I gues the answer is 'whatever'; efi.nottobeused, efi.ragnia1980, stupidefi

It should not matter what it's renamed to, as long as it does not already exist.

---

### Post by aeroditya on 2012-10-01
I am facing very similar problems on my new **Lenovo G580 **laptop 64-bit, dual booted with Windows 7 and Ubuntu 11.10.
After installing Ubuntu, I find myself stuck here, as my windows goes undetected. Please see my thread here and help me out - 
[http://ubuntuforums.org/showthread.php?t=2064761]("http://http://ubuntuforums.org/showthread.php?t=2064761")

According to your solution, do I have to rename efi folder from the live USB (using the try option), or can I just rename it from my current ubuntu session? Do I have to re-install Ubuntu? Please give a  more detailed procedure as I am very new to Ubuntu and this UEFI problem!

Thanks a lot!

---

### Post by ponciete on 2013-06-22
Absolutely Great!!! Big big thanks. Thre days fighting my Aspire 5560 to install Ubuntu and the problem is solved renaming the EFI folder.

---

