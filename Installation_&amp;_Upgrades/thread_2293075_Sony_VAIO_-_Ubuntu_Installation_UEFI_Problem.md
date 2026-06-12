---
title: "Sony VAIO - Ubuntu Installation UEFI Problem"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by wojtek132 on 2015-09-02
Hello.
I have a problem with Sony VAIO notebook (SVE14AA11M). It has preinstalled Windows 7 Home Premium.
I want to install Ubuntu next to Windows. I was installing Ubuntu from LiveDVD. I created new partitions from free space and installed Ubuntu here in UEFI mode. But after restart computer shows black screen, on which appears text:
> Booting in insecure mode.
Failed to open \EFI\BOOT\grubx64.efi - 800000000000000E
Failed to load image

Failed to open \EFI\BOOT\MokManager.efi - 800000000000000E
Failed to load image
Nothing else happens. I can only run Ubuntu from LiveDVD.
I study Computer Science but I am weak in repairing system etc.
I tried to repair this but without effects. I changed file names on efi partitions but text on black screen is same as before. 
I found that there are two EFI partitions.
What happens? What should I do now? Now I need to start either Windows or Ubuntu (not matter which). But in the end I want to have Grub (or similar) and choose Windows and Ubuntu.
Sorry for poor english.

Thank you for responses.

---

### Post by oldfred on 2015-09-02
Is Windows in UEFI boot mode?
Both Ubuntu & Windows need to be in same boot mode, both BIOS or both UEFI.
And if Windows was BIOS installing Ubuntu in UEFI may convert drive from MBR to gpt partitioning and create major issues for Windows.

Best to see details.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Sony will only boot Windows in UEFI mode. It modifies UEFI to include description in boot and only valid description is "Windows". That is not UEFI standard.
But there are several work arounds to get it to boot and depending on your configuration one may be better than the other.

---

### Post by wojtek132 on 2015-09-03
I think that Windows is in UEFI mode because there have been already two  EFI partitions before I have installed Ubuntu. Partitions have been in  GPT too.
Ubuntu was installed from USB. And I am almost certain that it was installed in UEFI mode.
I run Boot-Info now from Ubuntu LiveDVD. To boot from DVD I need to change to legacy mode in BIOS/UEFI.
Link to online report from Boot-Info:
[http://paste.ubuntu.com/12262753/](http://paste.ubuntu.com/12262753/)

---

### Post by wojtek132 on 2015-09-03
Link to online report from Boot-Info (USB, UEFI mode):
[http://paste.ubuntu.com/12263332/](http://paste.ubuntu.com/12263332/)

---

### Post by oldfred on 2015-09-03
You only have one ESP - efi system partition as sda3. But do have more efi boot files in sda1 which is not an ESP. Some vendors are able to boot recovery or repair or system configurations from a non-ESP partition. Grub2's os-prober also picked up those boot files as Windows boot. Note different UUIDs.

```
/dev/sda1        [COLOR=#ff0000]E6AF-2148[/COLOR]                              vfat       SONYSYS
/dev/sda2        FE36B29336B24D01                       ntfs       Recovery
/dev/sda3        [COLOR=#ff0000]389C-D6B7[/COLOR]                              vfat       


```
In details of Windows boot stanza in grub are the UUIDs.

All Sony that we have seen have modified UEFI to also use description and only valid description is "Windows". That is not UEFI standard.

Most with Sony copy grub or shim efi files into /EFI/Boot and rename one to bootx64.efi. That is a fallback or hard drive boot. It is standard for all external drives and can be used for internal drive. Sony's UEFI does not check description and it file is really grub then it boots.

Details: Also in link in my signature
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)

        One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

---

### Post by wojtek132 on 2015-09-05
I have tried some options. 
Moving shim file from ubuntu to Boot didn't changed anything. I have tried to install refind. But it says: 
> You've specified re-signing your rEFInd binaries with locally-generated keys.
Your  computer does not appear to be running in Secure Boot mode. The keys  you generate will be useless unless you enable Secure Boot.
Next I have moved refind file to Boot/bootx64.efi
I set description of bootx64.efi with efibootmgr, but problem still exists.
I will try another options.

Could someone explain why computer is "booting in insecure mode"? I don't have option in BIOS/UEFI to set secure mode.
And why computer are trying to load precisely these files (grub64.efi, MokManager.efi)?

Efibootmgr - boot order (maybe this information will help somehow):
> BootNext: 0003
BootCurrent: 000A
Timeout: 2 seconds
BootOrder: 000A,0005,0006,0007,0000,0002,0003,0004,0001,0009
Boot0000* Windows Boot Manager
Boot0001* CD/DVD Drive 
Boot0002* ubuntu
Boot0003* Windows Boot Manager
Boot0004* Windows Boot Manager
Boot0005* Sony Original
Boot0006* Windows Boot Manager
Boot0007* Windows Boot Manager
Boot0009* Hard Drive 
Boot000A* UEFI:  8.07

---

### Post by oldfred on 2015-09-05
There are three boot modes, but many UEFI do not make it clear.
UEFI with secure boot - only signed boot loaders & kernels will boot. Optional with Windows 8 or Ubuntu.
UEFI but unsigned or "un-secure" boot loaders & kernels will work. Required for Windows 7. Optional with Windows 8 and Ubuntu.
CSM where CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode      (is never secure boot)

Many have UEFI on, and then a secure boot setting or a CSM setting. Some just have a few settings and automatically switch to how system is installed.

It looks like you have several duplicate Windows settings, but normal UEFI from efibootmgr shows more details. Not sure then what UEFI: 8.07 entry is? Or does flash drive have a label of 8.07?

---

