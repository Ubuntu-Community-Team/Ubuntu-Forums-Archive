---
title: "Help with Installing Ubuntu on a Preinstalled Windows 8 Lenovo Laptop"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by hamsn on 2013-04-26
Hello there,

First let me describe the scenario.
It is a latest Lenovo laptop with Windows 8 Preinstalled. I tried disabling SecureBoot in the BIOS, and with SecureBoot enabled or disabled, the Windows 8 was still booting. Does this mean Windows 8 was installed with legacy mode and not in EFI mode?
Next, I have a Live USB drive with 12.10 64bit on board, I booted through it, installed alongside Windows 8, in the size selector I allocated about 60GB for Ubuntu, everything went well, until the next reboot. After reboot it gave a SecureBoot fail error, so I disabled SecureBoot in the BIOS and purged and reinstalled Ubuntu same as in previous way, and now after reboot it seemed like nothing was installed and the PC booted straight to Windows 8. I did everything following this guide: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I also tried booting the live Ubuntu and running the boot-repair, but it ends up saying there were errors, this is my url: [http://paste.ubuntu.com/5600719/](http://paste.ubuntu.com/5600719/)
When the boot-repair was working I saw something Wubi, and previous to my attempt on installing, the other person had tried installing with the Wubi Windows Installers, so this is the scenario, give me an idea where exactly it is messed up.

Thanks and regards!

---

### Post by oldfred on 2013-04-26
If Windows booted without secure boot on, that is good, as many systems only boot with secure boot on and you have to install Ubuntu with its signed versions. You at least have the option not to.
But some still have modified UEFI to only boot the Windows efi file. Boot-Repair has a work around if that is a problem

Your install of wubi will not work with UEFI. If looks like you did install it to separate NTFS partitions which you can delete or combine or convert to a NTFS data partition which you should have anyway dual booting.
 Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)



But you do have an issue we have seen with some systems and do not have a simple solution. From the last line of your BootInfo report.
Locked-ESP detected.


 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

Have not looked lately to see if any new solutions but the main solution was to backup the efi partition, which also is a good idea anyway. Delete it, recreate it from gparted, format fat32,  and add boot flag so it is a new efi partition and restore the Windows efi files. Then grub should be able to install its efi folder and boot files. Perhaps it is the Active Protection (see below)?

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)

---

