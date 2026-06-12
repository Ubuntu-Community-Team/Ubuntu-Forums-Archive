---
title: "System does not boot after fresh Ubuntu install and boot-repair."
date: 2017-11-19
forum: Installation &amp; Upgrades
---

### Post by lukewallis0 on 2017-11-19
I used the liveCD for Ubuntu 17 and installed the OS to a flash drive. When the computer boots, only a black screen shows. If I hold shift, the screen says "Grub loading." and hangs like that forever. I went back onto the liveCD and ran boot-repair. Here's the pastebin report: [http://paste.ubuntu.com/25994964/](http://paste.ubuntu.com/25994964/)

Any help would be appreciated.

---

### Post by oldfred on 2017-11-19
I am not seeing anything wrong with install.
Have you tried the recovery mode to see if it boots to command line. 
Or where in boot process it fails.

What brand/model system?
How much RAM?

Most desktops do not need a separate /boot partition. Some that use LVM or encryption do use a /boot partition.

---

### Post by lukewallis0 on 2017-11-20
System: HP Pavilion dv6-6b26us (a7w61ua#aba)
6GB RAM
Drive: Samsung 128GB USB 3.0 Flash Drive Fit

Recovery mode only shows "Grub loading" like I said, so I don't know anything about where in the boot process it fails. 

I know this drive *can* boot successfully because it operates just fine if its OS is the liveCD; however, if its OS is a standard Linux install, it will not.

It seems that other users with this kind of laptop and a Ubuntu USB installation discussed using the UEFI bootloader instead of the BIOS one. How do I make a UEFI installation?

---

### Post by oldfred on 2017-11-20
The installer is both UEFI or BIOS. And how you boot install media, is then how it installs.
You should get two boot options in UEFI menu for USB flash drive installer. Usually one is clearly UEFI and other just name or label of flash drive.
Boot of flash drive is normally separate from UEFI settings for boot of actual install.

For more info on UEFI install see link in my signature. You should just need the 9 steps to correctly install, but it has links to lots more info if issues or a step is not known on how to do it.
But many HP do have another issue as they violate UEFI standard and require a work around. OFten Boot-Repair fixes it, or we  have to move some files around.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 


You can make an UEFI only installer, it just does not include the BIOS boot loader.
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by lukewallis0 on 2017-11-21
OK. After further testing, I have determined this computer is BIOS only, no UEFI. I think what would solve the boot issue is using the extlinux bootloader, because GRUB has been known to struggle when booting a USB device. Is there a Linux distro that comes with extlinux instead of GRUB in its installer, or do I have to install extlinux manually?

---

### Post by oldfred on 2017-11-21
I never had trouble booting flash drives with full installs using grub.
But during install in BIOS mode you need to use Something Else and choose to install boot loader (grub) to MBR of same drive as your install. 
Then in BIOS select to boot that drive.

Boot-Repair's advanced option should let you choose install and drive to install boot loader into.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Advanced options screens:
       
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lukewallis0 on 2017-11-22
Hmmm. I just did you describe exactly, installing Ubuntu to the USB Drive, BIOS bootloader on it, standard partition setup, selected it as the boot option BIOS, and it doesn't work. The computer boots to a black screen, just like I said in the first post here, so I ran boot-repair. Here's the pastebin this time around: [http://paste.ubuntu.com/26017727/](http://paste.ubuntu.com/26017727/)

The final boot-repair window also mentions: "The boot files of [Ubuntu 17.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk) ..."

No boot. Black screen.

---

### Post by oldfred on 2017-11-22
The far from start of disk was an issue with old, now very old IDE BIOS that could not boot from from beyond 137GB. And some USB drives have similar issues.
But you should have drive set in BIOS to AHCI, not IDE, nor RAID. IDE may be trying to fully emulate to old limits.

And black screen issue is most commonly a video driver issue.
What video card/chip do you have? Script shows Intel second gen which usually just works.
Have you tried second line in grub menu or recovery mode (it includes nomodeset, but boots to command line).

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by lukewallis0 on 2017-11-23
The BIOS configuration utility is very limited, and there is no option for IDE/ACHI/RAID modes. Video card: Intel HD 3000 on Intel i3 2330M. I cannot access the GRUB menu to enable recovery mode, because it's just a blank screen; holding shift on boot makes "Grub loading." show up, but it hangs there forever. See video.

Video: [https://gfycat.com/gifs/detail/BreakableTatteredBeetle](https://gfycat.com/gifs/detail/BreakableTatteredBeetle)

---

### Post by oldfred on 2017-11-23
If an i3 then it is UEFI, but early version if chip is 2330 series.
Have you updated UEFI to latest version from your vendor.
Many early UEFI also needed updates to work with Linux.

---

### Post by lukewallis0 on 2017-12-03
I updated the BIOS to the latest available version F.1C in the past, but I don't know how exactly I'd go about updating the UEFI besides that. There are a few UEFI tools available from the driver downloads page, but I can only get the hardware diagnostics one to work. The other utilities "HP Unified Extensible Firmware Interface (UEFI) Support Environment", and "HP UEFI Support Environment" I can't get to load.

---

### Post by oldfred on 2017-12-03
If you want to stay with BIOS as that is an early UEFI system that may work better. I do prefer UEFI and in particular prefer gpt partitioning. 
You can use gpt even with BIOS boot of Ubuntu, but not if you want to boot Windows in BIOS mode. Windows can only boot in BIOS mode from MBR and only in UEFI mode from gpt.

But in UEFI/BIOS you have to turn off UEFI boot and turn on BIOS boot.
       HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

---

### Post by lukewallis0 on 2018-01-31
So, I revisited this deadly combo of HP + USB + GRUB and it seems impossible. 
What actually worked for me was this process:
1. Run the livecd installation process onto the destination USB drive.
2. Start up the recently installed Ubuntu USB drive in a compatible (non-HP) computer.
3. Install syslinux/extlinux and replace GRUB, then remove the USB drive and put it in the HP computer.

After doing that, I had the workable combo of HP + USB + EXTLINUX, which really boots!

---

