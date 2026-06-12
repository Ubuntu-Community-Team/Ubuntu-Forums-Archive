---
title: "disabling UEFI &amp; secure boot"
date: 2024-11-23
forum: Installation &amp; Upgrades
---

### Post by garyed on 2024-11-23
I'm trying to install Ubuntu 24.04 as a dual boot on a laptop with Windows 10 from a bootable USB flash drive. 
I used "Start up disk creator " to make the USB boot flash drive. 
The flash drive will only boot if I disable UEFI & secure boot in the BIOS which is easy enough to do.
When UEFI & secure boot are disabled then the Windows boot option will not even show up in the BIOS.
What I'm concerned about is if I go ahead & install Ubuntu from the flash drive that I will not be able to get Windows to boot back up. 
Can anybody shed a little light on the matter?

---

### Post by tea for one on 2024-11-23
> **garyed said:**
> The flash drive will only boot if I disable UEFI & secure boot in the BIOS which is easy enough to do.
When UEFI & secure boot are disabled then the Windows boot option will not even show up in the BIOS
I am writing this reply from a live session of Ubuntu 24.04 with both TPM and Secure Boot enabled.
Ubuntu 24.04 live session should boot with TPM and Secure Boot enabled.
Try another flash drive or another USB port.

Having written that, as a home user, I always disable TPM and Secure Boot.
Installed Windows 10/11 and Ubuntu 22.04/24.04 always boot whether TPM/Secure Boot is enabled/disabled
> **garyed said:**
> What I'm concerned about is if I go ahead & install Ubuntu from the flash drive that I will not be able to get Windows to boot back up. 
Can anybody shed a little light on the matter?
Install Ubuntu and see what happens?
Your new Ubuntu can easily be removed and you can always re-enable Secure Boot and TPM.
Your Windows OS should be unaffected if you are careful with partitioning.
It is better to use Windows tools to create free space.

---

### Post by yancek on 2024-11-23
Any Ubuntu recent release should be able to boot in UEFI mode.  What exactly happens when you try to boot the Ubuntu USB in UEFI mode?  Which iso of Ubuntu did you download?  After downloading the Ubuntu iso, did you do a checksum to verify that it was not corrupted during the download?  Are you going to install Ubuntu to the same physical drive on which you have windows?   If you install Ubuntu in Legacy mode and windows is UEFI and they are on separate physical drives, you should be able to boot windows from the Ubuntu Grub bootloader.  If they are on the same drive, you will not be able to boot windows UEFI from a Legacy install of Ubuntu.

---

### Post by tea for one on 2024-11-23
> **garyed said:**
> The flash drive will only boot if I disable UEFI & secure boot in the BIOS which is easy enough to do.
When UEFI & secure boot are disabled then the Windows boot option will not even show up in the BIOS.
What I'm concerned about is if I go ahead & install Ubuntu from the flash drive that I will not be able to get Windows to boot back up. 
Can anybody shed a little light on the matter?
Oh, reference post 2, I completely misread UEFI and substituted TPM in my head.........reminder to myself to pay more attention.

Your Windows 10 OS is installed in UEFI mode and will be unavailable if your disable UEFI on your PC.
Ubuntu 24.04 (live session and installed) will definitely boot in UEFI mode.
Did you try a different USB port?

---

### Post by garyed on 2024-11-23
> **yancek said:**
> Any Ubuntu recent release should be able to boot in UEFI mode.  What exactly happens when you try to boot the Ubuntu USB in UEFI mode?  Which iso of Ubuntu did you download?  After downloading the Ubuntu iso, did you do a checksum to verify that it was not corrupted during the download?  Are you going to install Ubuntu to the same physical drive on which you have windows?   If you install Ubuntu in Legacy mode and windows is UEFI and they are on separate physical drives, you should be able to boot windows from the Ubuntu Grub bootloader.  If they are on the same drive, you will not be able to boot windows UEFI from a Legacy install of Ubuntu.

It's an Acer laptop & when the bios is set to UEFI secure boot then the usb drive gets bypassed during boot up even though all USB devices are set to boot before Windows. 
It will still boot straight into Windows unless I change the bios to Legacy which automatically disables secure boot.
I'm doing this for a family member & now I don't have access to the computer any more so I'm going to have to give advice over the phone.
I don't remember having this problem installing Ubuntu on my Desktop With windows in UEFI mode so I'm not sure how to tell them to proceed.

---

### Post by tea for one on 2024-11-23
Isn't Acer the brand where you have to enable Trust in the UEFI settings somewhere?

---

### Post by yancek on 2024-11-23
Many newer Acer computers require the 'enable trust' option which I believe requires a supervisor password in the BIOS.  You might just do an online search on how to set it.

Found the link below which explains the process.

[https://community.acer.com/en/kb/articles/88-enable-or-disable-secure-boot-on-an-acer-notebook](https://community.acer.com/en/kb/articles/88-enable-or-disable-secure-boot-on-an-acer-notebook)

---

### Post by oldfred on 2024-11-23
What model Acer?
[https://ubuntuforums.org/showthread.php?t=2468820](https://ubuntuforums.org/showthread.php?t=2468820)
Acer Swift 3 SF314-511 Enable USB boot F12
[https://ubuntuforums.org/showthread.php?t=2475752](https://ubuntuforums.org/showthread.php?t=2475752)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

---

### Post by ubfan1 on 2024-11-23
Another thing to check: even though you have USB first in the boot order, there may be another ordering under "UEFI hard disks", which for some unknown reason may enumerate the USB device.  Put the USB first in that list also.

---

### Post by garyed on 2024-11-23
> **oldfred said:**
> What model Acer?
[https://ubuntuforums.org/showthread.php?t=2468820](https://ubuntuforums.org/showthread.php?t=2468820)
Acer Swift 3 SF314-511 Enable USB boot F12
[https://ubuntuforums.org/showthread.php?t=2475752](https://ubuntuforums.org/showthread.php?t=2475752)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

I don't know what model Acer but it's an older model that came with Windows 7
I had to leave & get back home from where I was so I didn't have much time to deal with this. 
I was thinking there might be some special way to make a boot usb drive that would work in UEFI mode but it seems like it's more of an Acer bios problem. 
I'm going to try & make another boot usb flash drive the exact same way & see if it boots on my UEFI system at home.

---

### Post by oldfred on 2024-11-23
Most Windows 7 systems were BIOS with MBR partitioning.
Windows 7 as downgrade to Windows 8 or some later installs may be UEFI as vendors started using UEFI as replacement for BIOS.
Microsoft required vendors to install Windows 8 in UEFI boot mode with gpt partitioning starting in 2012.

---

### Post by garyed on 2024-11-24
> **oldfred said:**
> Most Windows 7 systems were BIOS with MBR partitioning.
Windows 7 as downgrade to Windows 8 or some later installs may be UEFI as vendors started using UEFI as replacement for BIOS.
Microsoft required vendors to install Windows 8 in UEFI boot mode with gpt partitioning starting in 2012.

I probably shoud have clarified things a little better. 
The laptop was originally Windows 7 but had been upgraded so it is now running Windows 10. 
I wanted to give an idea of how old the computer was so that is why I brought up that it wcame with Windows 7. 
I just checked the bios on my home computer & it is set to both UEFI & Legacy but the bios on the laptop in question can only be set to either Legacy or UEFI.
I'm out of empty usb flash drives but I'm going to get one & test it with the bios set to UEFI only out when I get chance. 
That might tell me if it's a bios issue or an Acer issue or something else. 
My main concern is if I can only get the flash drive to boot in legacy mode can & I still install Ubuntu in UEFI mode so Windows 10 will still work.

---

### Post by oldfred on 2024-11-25
All systems require UEFI boot for UEFI install whether Windows or Ubuntu.
Some older Dell required BIOS/CSM/Legacy mode on, but you still chose the UEFI boot option on the USB live installer. New systems since about 2020 do not even have a BIOS/Legacy option, they are UEFI only.

It becomes a bit tricky to install in BIOS mode & convert to UEFI, but can be done.
Its just that I do not know what installer will do by default.

The only real difference between UEFI & BIOS installs is the version of grub and setting in fstab that is normally changed if grub version changed.

With Windows in UEFI mode drive has to be gpt. Installer should create a tiny bios_grub partition as required for grub in BIOS mode on gpt partitioned drives.

Grub for BIOS is grub-pc, but you can uninstall it and install grub-efi-amd64. That requires an ESP - efi system partition, but it will share the Windows ESP.  If during uninstall, the reinstall does not work, system will not boot. Then you need Ubuntu live installer to repair. Boot-Repair in advanced mode or a full chroot into system to install grub.
If you first add the mount of ESP to fstab, and the grub-efi-amd-64 package is installed, it may just reinstall grub automatically in UEFI mode.
Normally grub install requires parameters, but I can reinstall on my UEFI system with just a simple sudo grub-install command and it uses a lot of defaults, particularly the mount of the ESP in fstab.

---

### Post by garyed on 2024-11-25
Well I finally tried a fresh usb flash drive & created a bootable drive from the exact same iso file I made the other one from so I could test it out on my desktop at home. 
It boots up fine whether I set the BIOS to legacy mode only or UEFI mode only so there's nothing wrong with the iso or boot usb flash drive. 
The problem is definitely with either the Acer laptop or it's bios that will only let the usb flash drive boot in legacy mode. 
So I go back to my original question knowing that Windows 10 boots in UEFI mode on the laptop. 
Can I set the bios to boot legacy & install Ubuntu in UEFI mode along side the existing Windows 10 in UEFI mode & then change the bios back to UEFI mode to get things working?

---

### Post by hifron on 2024-11-26
As you could see in [Debian]("https://wiki.debian.org/SecureBoot"), Secure Boot is technology unknown and not made for humans but for machines and their mood and if Ubuntu or some vendors do something with, even better.

---

### Post by yancek on 2024-11-26
Have you tried booting the USB from different ports?  I had an Acer some years ago which had  USB ports but only booted from one.  Have you had a chance to follow the instructions in post 7 (the link posted) to enable trust with a supervisor password?  

>  Can I set the bios to boot legacy & install Ubuntu in UEFI mode  along side the existing Windows 10 in UEFI mode & then change the  bios back to UEFI mode to get things working? 		

No, don't think that will work as the manner in which it is boot is the manner in which it is installed so if you boot in Legacy mode, it will install boot code to the MBR and there will be nothing related to Ubuntu on the EFI partition where the system board looks for boot files.  You could install Ubuntu Legacy and boot windows EFI but only if they are on separate physical drives which I do not believe is your case.

---

### Post by oldfred on 2024-11-26
See post #13 on converting BIOS install to UEFI.

While you cannot boot Windows in BIOS mode & Ubuntu in UEFI mode on same drive, you may be able to boot Windows in UEFI mode & Ubuntu in BIOS mode. But probably a hassle, as with most older systems you have to change boot mode in settings to boot install in that mode. Newer system know which mode boot entry is in, will then boot in that mode.

---

### Post by garyed on 2024-11-26
I already tried booting from different usb ports but that didn't help. Now I don't even have physical access to the laptop so I'm pretty well stuck now. 
If it was my Acer laptop that I was trying to install Ubuntu in a dual boot situation then I could do some experimenting but in this case it's not. 
It's a family member's laptop & now it will pretty much have to be done over the phone so I'm hesitant to even try anything without being 100% sure it will work.

---

