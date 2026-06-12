---
title: "DualBoot Grub problems"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by jonasmarx on 2018-07-27
Hello!

I have a PC with two hard drives and UEFI-Bios, one with Windows 7, the other one with Ubuntu. I wanted to have a fresh install of Ubuntu 18.04. and grub on the second one, where i can switch. After the fresh install, grub didn't recognize the Windows installation. So i tried boot-repair. It said that i have a GPT formatted hard drive and i should reformat it as boot_bios. But when i try that or a traditional MBR with /boot partition, grub-efi-amd64-signed cant get installed. Right now im at a point where grub recognized the windows install (i got here after hours of different partitionings and diverse boot-repairs), but getting the error "harddrive hd0, msdos1 not found".

Could someone explain me how grub can recognize the windows harddrive? I really tried a lot and none of the googled results worked for me..

So what i tried already:
- Installing ubuntu on MBR partitioned drive -> Error on install
- Installing Ubuntu on GPT partitioned drive -> doesnt recognize windows, boot-repair wants me to change to old /boot style again
- boot-repair -> first time changed nothing, now Ultimately Windows 7 was recognized but not found when selected in grub
- added Windows 7 as custom_40 to grub -> not found as well

---

### Post by oldfred on 2018-07-27
You have to be consistent.
Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR partitioned drives with BIOS.
And you want Ubuntu in same boot mode as Windows.

So if Windows is UEFI boot on gpt partitioned drive, you want Ubuntu in UEFI boot mode.
If you see request for bios_grub partition that is for BIOS boot on gpt partitioned drive. Ubuntu can boot in either UEFI or BIOS from gpt.
So be sure to boot installer in UEFI mode.
Also with 2 drives you need to partition in advance. Best to have an ESP on second drive, even though any UEFI install will not use it.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
      [/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by jonasmarx on 2018-07-27
Thank you, oldfred!
So the windows hard drive is formated as msdos partition and as far as i understand, in the BIOS/UEFI setup, secure boot is disabled.
So theoretically, i'd install ubuntu as MBR and traditional /boot setup, right?

But actually, since UEFI is more and more getting standart, maybe i need to setup Windows as GPT install as well... What would you recommend? Btw: When i had the old Ubuntu 17.10. install, Ubuntu took forever to boot, when windows just needed some seconds, so it's not about my machine is too slow in general..

Greetings,
Jonas

---

### Post by oldfred on 2018-07-27
It is very complicated to convert Windows as you have to change partitioning which in effect erases partitions. Windows recently released some tools to convert partitioning. But no idea what changes required to convert to UEFI boot.
With Linux you can use gdisk to convert from MBR to gpt or vice  versa, but have to reinstall the grub2 boot loader from grub-pc for BIOS to grub-efi-amd64 for UEFI.

You can dual boot with one UEFI and one BIOS, but then cannot use grub to dual boot. Once you start booting in one mode, you cannot change. Or once to grub menu, grub can only boot other installs that are in same boot mode. You still can dual boot from UEFI boot menu every time.

Long before I had UEFI system, I started converting drives to gpt. And when Windows required UEFI/gpt with Windows 8 from vendor, I started adding both  an ESP - efi system partition for future and bios_grub for current boot. Then I could move drive to UEFI system and just reinstall grub, rather than totally erase, convert & reinstall.

You do not need nor want a /boot partition. It is used with some server installs or LVM, but not required with most desktops.

Also 18.04 now uses a swap file (like Windows) rather than a swap partition. If a swap partition found during install it will find it and use it. My test install of 18.10, I was able in Something Else select swap partition that I still have and select it as do not use. It then did not use swap partition and created swap file.

Whatever you do have good backups. But most do an image backup of Windows and that would be BIOS/MBR, so if restored it would still be a BIOS install. 

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations

      [/URL]
 Convert Windows from BIOS/MBR to UEFI/gpt.
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)
[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]
[/URL]

---

### Post by jonasmarx on 2018-07-29
Okay. So of course my original plan was to keep the windows install and make the Ubuntu install in the same mode, but that didnt work for reasons.
Now my final solution was to whipe everything and install both from ground up based on GPT. Now grub found the windows install. Thx for help.

---

