---
title: "Lubuntu/Windows 10 Dual boot from separate drives (noob questions/concerns)"
date: 2021-04-01
forum: Installation &amp; Upgrades
---

### Post by sircanucklehead on 2021-04-01
Hi all, I'm pretty new to linux in general, and have been reading up on the process of setting up a Win10/Linux dual boot over the last couple days, but some things are still unclear to me.

I want to install Linux on it's own HDD to keep everything separate from Windows. So my drive setup would be;

-1tb SSD with Windows 10 installed

-2tb HDD for storage for Windows 10

-1tb HDD for Lubuntu install/storage.

My goal is to choose between Win10 or Lubuntu on each startup, but I'm not sure exactly how to accomplish that (I've read up a bit on GRUB but I'm not positive on how/where to install it, ie during Lubuntu install, after it's installed, etc).

I just unplugged all my Win10 related drives and tried installing Lubuntu on the 1tb HDD for fun, but I didn't end up finishing because there are some things I'm just not clear on. For one, the partitioning; I'm on the legacy BIOS setting for Win10, so I'd have to make an MBR partition table(?) on the 1tb HDD. For a dual boot, what would be the partitioning setup so that I can access GRUB on each startup? Would I have to change my BIOS settings to boot from the drive with Lubuntu installed in order to access GRUB, to then pick either Win10 or Lubuntu?

I've found a bunch of tutorials on how to do a separate drive dual boot with Ubuntu, but none with Lubuntu. I tried to follow those guides as best I could, but the Calamares installer has it's own set of options vs Ubuntu's Ubiquity installer, and I just didn't want to make assumptions and screw something up.

Anyway, I'm hoping someone could just point me in the right direction. If I didn't give enough info, please just let me know what to add and I'll do so. Many thanks.

---

### Post by CatKiller on 2021-04-01
> **sircanucklehead said:**
> .My goal is to choose between Win10 or Lubuntu on each startup, but I'm not sure exactly how to accomplish that (I've read up a bit on GRUB but I'm not positive on how/where to install it, ie during Lubuntu install, after it's installed, etc). 

That's a fairly standard setup. Even if you mess it up, it will happen automatically: whenever Grub updates your bootloader image, it will probe for other OSes to add to the menu that it creates. 

Windows denies the existence of any other OS, but as long as you use the Grub bootloader rather than Windows' you'll be fine. 

> For one, the partitioning; I'm on the legacy BIOS setting for Win10, so I'd have to make an MBR partition table(?) on the 1tb HDD. 

It's easier if you aren't doing that. BIOS is ancient and extremely limited, and MBR is full of weird quirks. With UEFI and GPT you can have an EFI System Partition that's as big as you like where all the bootloaders can co-exist happily. With BIOS/MBR you have a tiny slice in the Master Boot Record that will hold some executable code that will chainload the remaining stages of the bootloader, and other bootloaders. Since you only have a tiny amount of space, it's limited in what it can do, makes it harder to find the remaining stages, and - because you can only have one - runs the risk that Windows will stomp all over it with an update. 

> Would I have to change my BIOS settings to boot from the drive with Lubuntu installed in order to access GRUB, to then pick either Win10 or Lubuntu? 

For BIOS/MBR, yes. You'd tell your BIOS to boot the bootloader contained in the MBR, and you'd want that to be your new Linux drive. You *can* install Grub to the MBR of your Windows drive, but then the drives will be linked: you wouldn't be able to boot either without the other. As you are now the bootloader in the MBR of your Windows drive can boot Windows, so putting Grub in the MBR of the Linux drive will let you boot Linux or Windows; if you remove the Windows drive the Linux drive will still be able to boot, and if you remove the Linux drive the Windows drive will still be able to boot. 

UEFI/GPT is way easier. Having all your bootloaders in one ESP (which is conceptually simpler) or several makes no real difference.

---

### Post by sircanucklehead on 2021-04-01
Thanks for the info. So, just to make sure I've got it straight, I should convert to UEFI, install Lubuntu on my other HDD, GRUB will install automatically with it, and then I can dual boot?

The one part I'm still not clear on is making sure I have GRUB set up. I saw a partition flag in Calamares labelled something along the lines of /grub or /grub-boot, would I be making that my first partition?

---

### Post by CatKiller on 2021-04-01
> **sircanucklehead said:**
> So, just to make sure I've got it straight, I should convert to UEFI, install Lubuntu on my other HDD, GRUB will install automatically with it, and then I can dual boot?

If by "convert to UEFI" you understand that as "boot in UEFI mode rather than Legacy/CSM and reinstall Windows," then yes, otherwise no. If you're booting UEFI you wouldn't be able to boot your BIOS Windows install.

UEFI is better than BIOS and is easier in lots of ways, and is the default for Windows from around Windows 7, but whether you want to reinstall Windows after you've been using it the old way is something that you'd have to decide for yourself.

If you want to keep using Windows in BIOS mode you'll want to install Linux in BIOS mode. If you're going to install Windows in UEFI mode (or nuke it entirely) you can install Linux in UEFI mode. As long as they're all the same you should be fine, and Grub will be able to find Windows to add it to the boot menu. 

I've never installed Lubuntu so I have no experience with the installer. Other people here have, though, so they'd be able to help with any specific issues.

---

### Post by sircanucklehead on 2021-04-01
Okay, I think I understand. In doing some research I've found that you can convert from BIOS to UEFI without loss of data (without reinstalling Windows), which is apparently a newer feature of Win10 ([https://www.maketecheasier.com/convert-legacy-bios-uefi-windows10/](https://www.maketecheasier.com/convert-legacy-bios-uefi-windows10/))

I'll ask around for specific details on the Lubuntu installer just to make sure I'm not missing anything with the partition setup. Again, I appreciate the help.

---

### Post by guiverc on 2021-04-01
> **sircanucklehead said:**
> 
I'll ask around for specific details on the Lubuntu installer ...

You didn't provide any [Lubuntu] release details.

Lubuntu ***currently*** has three supported installers

- `calamares` used by all *modern* releases of Lubuntu
- `ubiquity` used by *legacy* releases
- *debian installer` *also available for *legacy* releases when using the *alternate* ISO

The installer is decided by which release, and which ISO you use to boot & install the system. You didn't provide release details, though I'd recommend `calamares` and a *modern* release as the other releases reach EOL this month.

---

### Post by yancek on 2021-04-02
>  I'm on the legacy BIOS setting for Win10, so I'd have to make an MBR partition table(?) on the 1tb HDD 

Are you positive about that?  Did you install windows 10 yourself or have someone do it for you?  A default windows 10 install from the manufacturer will almost certainly be UEFI/GPT.

>  For a dual boot, what would be the partitioning setup so that I can  access GRUB on each startup? Would I have to change my BIOS settings to  boot from the drive with Lubuntu installed in order to access GRUB, to  then pick either Win10 or Lubuntu?


Absolutely.  If your windows 10 is in fact, a Legacy/CSM install, then you will need to install Lubuntu Legacy/CSM with an msdos partition table.  If you install Lubuntu EFI and your windows 10 is Legacy/CSM, the Lubuntu Grub will not boot windows.  If you install Lubuntu Legacy/CSM and windows 10 is actually EFI, the Lubuntu Grub will not boot windows.  Verify that first.

UEFI/GPT is better, no doubt about that.  I would definitely have a complete backup of the entire windows system before messing with converting to UEFI/GPT.

For this to work the way you intend, having Lubuntu Grub boot both Lubuntu and windows, you will always need to 1TB drive with Lubuntu attached and set to first boot priority in the BIOS.  Best option would be to disconnect the other drives before installing Lubuntu on the 1TB.  If that installation is sucessful, then reattach the other drives and run:  sudo update-grub from Lubuntu.

---

### Post by oldfred on 2021-04-02
If a separate drive, you can install Ubuntu in BIOS boot mode to gpt partitioned drive.

Windows in BIOS boot mode requires MBR, and in UEFI requires gpt.
Ubuntu will boot in either BIOS or UEFI from gpt, if you have correct supporting partitions for boot loader code.
UEFI requires an ESP - efi system partition as FAT32 300 to 500MB and BIOS requires bios_grub as unformatted 1MB.

I was booting XP in 2010 on BIOS and converted my first drive to gpt for Ubuntu and dual booted. XP on MBR & Ubuntu on gpt.
When Windows required UEFI, so new hardware would be UEFI, I started adding both bios_grub partition for my current BIOS system but also added an ESP to all new or repartitioned drives, so I could easily move drive to a new UEFI system.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

