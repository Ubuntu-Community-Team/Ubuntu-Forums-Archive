---
title: "Grub and uefi Partitions"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by Quarkrad on 2016-05-12
I was running ubuntu 14.04 and windows 10 on my uefi pc without any problems - I have just replaced 14.04 with Mate 16.04 via a clean install.  When I rebooted the grub screen told me I had win7 (pointing to a different hd - I have three); I updated grub but it made difference.   I can go into bios and via the efi screen boot to either ubuntu (mate) or windows 10 and it all works - it is just the grub screen that is wrong.  First of all I tried the Boot Repair disk using the default options - but it tells me ubuntu is not compatible with efi.  I would appreciate some help before I type anything in the Terminal as I can see me messing things up big time.

---

### Post by yancek on 2016-05-12
Run boot repair again and this time just select the "Create BootInfo Summary" option and post a link to the output here and someone should be able to help.

---

### Post by Quarkrad on 2016-05-12
Thank you.  Attached is my boot info.

---

### Post by Bucky Ball on 2016-05-12
> **yancek said:**
> Run boot repair again and this time just select the "Create BootInfo Summary" option and post a link to the output here ...

For future reference, post the link. When you the Boot Repair Bootinfo has run, it gives you a link. All you need to do is copy/paste that here.

At a guess you have installed Ubuntu on sda8 in legacy mode when Windows is in UEFI. From your output.

> You have installed on sda8 a Linux version which is not EFI-compatible.

That won't work. Install Ubuntu again on sda8 in UEFI. You need to use the 64bit ISO as far as I'm aware.

---

### Post by oldfred on 2016-05-12
You have sda as gpt which is the UEFI standard and required for drives over 2.2TiB.

But sdb & sdc are MBR(msdos) partitioned. 

Once you have UEFI hardware and use UEFI, better to start converting all drives to gpt when new, or totally reformatted. Not required immediately but something you should plan on.

I actually started converting drives to gpt with 10.10 as I knew evenually I would get a new UEFI system.
But Windows only boots from gpt with UEFI and only from MBR with BIOS, so back then my Windows drive was MBR, and Ubuntu was gpt, but still BIOS boot.

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

### Post by Quarkrad on 2016-05-12
Doh - sorry.  When I first set this hd up I installed win10 on it am I'm sure the disk was GPT (I guess it is by definition re: win10) - followed by 64bit ubuntu 14.04.  So it is the case that by reinstalling ubuntu mate (64bit version) onto sda8 everything will be OK?

---

### Post by oldfred on 2016-05-12
If Ubuntu on gpt drive in BIOS boot mode, Boot-Repair can convert to UEFI boot.

All it really does is uninstall grub-pc and install grub-efi-amd64 which internally changes some settings.

With multiple drives best to not use auto fix in Boot-Repair as it in BIOS mode installs grub to the MBR of every drive. With an UEFI system in UEFI boot mode having grub in MBR is not an issue unless you attempt to boot in BIOS mode as then it will not work. Unless you only want BIOS boot.

Best to always be consistent. Or always UEFI or always BIOS. But since Windows only boots in UEFI mode from gpt partitioned drive and you have Windows in UEFI mode, you should always boot Ubuntu & live installers in UEFI boot mode.

---

### Post by Quarkrad on 2016-05-12
Reinstalled 64bit version and then ran update-grub and all is working - thank you for your help.

---

