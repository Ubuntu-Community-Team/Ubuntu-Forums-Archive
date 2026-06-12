---
title: "boot in EFI mode"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2015-08-20
While installing Ubu 15, I accidently pressed f4 instead of f2 at boot and went into Windows recovery. Normally not a problem. Now, if I set boot mode to UEFI, only Win is available. It is not possible to choose any other option, viz a viz boot from a usb stick. I can only boot usb when I set UEFI + CSM mode in the bios.

Following instructions from the link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) I used apt-get on a Live usb stick Ubuntu15 iso to get Boot Repair and then ran it. 

I cannot boot the usb stick Live iso in UEFI mode. If I set UEFI mode,  only Win boots. So I set boot mode UEFI + CSM The boot stick boots, I  run Ubuntu, Boot Repair runs for a while then says:

"The current session is in Legacy mode. Please reboot the computer, and  use this software in an EFI session. This will enable this feature. For  example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode."

Question: with the boot mode set to UEFI + CSM is it possible to force  the system to boot UEFI? Only then will I be able to run Boot Repair and  maybe then it will do its stuff.

To complicate matters:

I made a Boot Repair usb stick with UNetbootin, from the bootrepair64bit iso. It too cannot boot if boot mode is set to UEFI 

I have fast bios mode = disabled, secure boot = disabled

 It boots when I set the mode to UEFI + CSM. Then I get the error

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: invalid argument

Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Tried all the options in the initial boot repair menu, same result, including failsafe.

Any tips out there? Wipe out the disc and start from fresh? But that would not affect the bios, would it?

Here is boot repair info. You can see /dev/sda3, 7 and 10 seem to have problems, and they are win related partitions.

[http://paste.ubuntu.com/12105967/](http://paste.ubuntu.com/12105967/)

---

### Post by oldfred on 2015-08-20
Your install in sda11 is a BIOS boot install. It uses the gpt protective MBR, and the bios_grub partition for grub2's boot not the efi partition for UEFI boot.
But the install in sda8 shows the efi partition in fstab, but Summary report is not showing any grub boot files in ESP - efi system partition.

What brand/model system?
Some require extra settings in UEFI to enable UEFI boot from USB ports. My Asus motherboard required UEFI only setting to get it to boot flash drive in UEFI mode.
Boot-Repair should offer to install or uninstall/reinstall grub2 in UEFI mode in advanced mode.

---

### Post by Pedroski55 on 2015-08-21
This is a Samsung E book 2 with AMD E2-1800 APU processors. It came with Win 8.1, which installs itself on first start. I need Win for my online bank, this is China, and it only works with Win and IE. I can start Win simply by changing boot mode to UEFI, but before Win was nicely installed in the grub boot menu. Think this trouble was caused by a recovery failure when I accidently pressed f4 instead of f2

As above, Boot Repair will not do anything when boot mode is set UEFI + CSM, and will not boot in UEFI. There is no way to get the usb to boot in UEFI that I can find. Tried all options.

---

### Post by oldfred on 2015-08-21
Have not seen too many with Samsung.

I think Boot-Repair's advanced mode in BIOS boot will still offer to uninstall grub-pc  and install grub-efi-amd664.

Most of these are older and I do not know if someone gives a clue on USB boot. Many issues have been resolved with newer versions of Ubuntu. Have you installed the newest version of UEFI/BIOS from Samsung?

 Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by Pedroski55 on 2015-08-22
Thanks very much, I'll read up on it!

---

