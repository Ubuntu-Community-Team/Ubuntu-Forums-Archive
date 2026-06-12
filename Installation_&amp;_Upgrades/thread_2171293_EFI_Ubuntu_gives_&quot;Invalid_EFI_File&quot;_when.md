---
title: "EFI Ubuntu gives &quot;Invalid EFI File&quot; when trying to boot Windows 7 legacy"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by Der_Scuple on 2013-08-30
Hi guys, I'm new here - I've been creeping the forums for a similar problem for several hours now but have not found a situation similar to my own, basically it goes like this:

Drive 0 is a 500GB Windows 7, 64 bit. For whatever reason, the installer set up the partitions in legacy mode.

Drive 1 is a 400GB Ubuntu 13.04, 64 bit. This installer installed with EFI mode.

I can easily switch between Windows and linux by altering the boot order through my BIOS, but what I really want to do is to be able to load Linux through the Windows boot, (Which I've had some trouble with already) or boot Windows through Linux. (Which I've had some success)

So far, the closest I've come to having this work is having Windows 7 appear on the grub screen at boot, but when I select it, I get an error "Invalid EFI file" probably something to do with the fact Windows is in legacy mode. 

I have no idea how to install Ubuntu in legacy mode, and have read several articles on converting, but don't want to go any further till I get some opinions?

Any help would be awesome!

---

### Post by oldfred on 2013-08-30
As you have found, you can only dual boot from UEFI menu when one install is UEFI and the other BIOS. UEFI & BIOS write hardware system info differently for operating system to use, so you cannot dual boot from grub menu. 
Grub2's os-prober creates the chain load entry but it will never work.

Since Windows is in BIOS mode it probably is easier to convert Ubuntu to BIOS mode. And Ubuntu will boot from a gpt partitioned drive in BIOS mode, so partitioning does not have to be changed. You will need a tiny 1MB unformatted partition with the bios_grub flag for grub to install correctly. It can be anywhere on drive. Use gparted to create new partition before running Boot-Repair.


Then use Boot-repair booted in BIOS mode and have it convert install. It uninstalls grub-efi and installs grub-pc.
I might leave efi partition on drive in case you every want to use UEFI later. It is not large so not much space lost.

I do not have UEFI, but boot Ubuntu from a gpt partitioned drive since 10.10 and back then had XP on another MBR drive and dual booted without issue. (ok a few issues as I was early with gpt and needed extra boot parameters). 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Der_Scuple on 2013-08-30
I was worried that was my only option.

Well - I ended up going into my motherboard BIOS and just setting my boot option to "Legacy Only" and reinstalling Ubuntu. 

Now it all works. I set HD2 (linux) as the primary drive, and now i get a nice boot list of my Ubuntu and Windows 7. (and memtest for whatever reason)

I think the big issue in my case was the fact my motherboard, by default, has the boot option to "UEFI and Legacy" allowing the Operating System to choose whichever mode it wants, in Windows 7 case, it went with legacy, and with Ubuntu, it went with EFI. Kind of frustrating if you ask me. The motherboard should force EFI or legacy, not "both". Just causes a mess for Multi-drive OS installations.

---

### Post by oldfred on 2013-08-30
Some users have posted that their UEFI is pretty clear on UEFI with secure boot, UEFI only or CSM/BIOS. 
But others try to simplify it by just having UEFI with secure boot and everything else automatically. 

Ubuntu's installer works with both UEFI and BIOS so UEFI should offer both choices but each system seems different and even different models by same vendor may be different.

---

### Post by Der_Scuple on 2013-08-31
It seems my motherboard software is in the "simplify" category. The only boot options it has are "UEFI or legacy, UEFI only, legacy Only" by default it was set to 'UEFI or legacy' which caused this whole mess in the first place. I wish I would of known when I first built my machine so I could of set the boot option to "UEFI only" and forced win 7 to install with the new setup.

---

