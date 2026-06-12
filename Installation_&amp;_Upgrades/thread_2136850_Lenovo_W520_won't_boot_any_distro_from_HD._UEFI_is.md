---
title: "Lenovo W520 won't boot any distro from HD. UEFI is turned off and legacy mode is on."
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by lolThisIsMyName on 2013-04-18
I've tried Ubuntu, Mint, etc. No luck with any of them. The live CD works fine. I've tried this with 2 different hard drives, no luck. UEFI is turned off and legacy mode is on. I've tried turning nVidia Optimus off too. All I get is a blinking cursor. Can anyone help me? I was under the impression that the W520 is very Linux friendly, so far this has been pretty discouraging. Any help would be appreciated.

Thanks,
-lolthisismyname

---

### Post by papibe on 2013-04-18
Hi lolThisIsMyName.

What version of Ubuntu are you trying to install? For 12.04.4 it is not necessary to disable UEFI BTW.

What is the size of you HD? If it is bigger than 2TB you may need to create GPT partition table with a special grub partition to boot form it.

Regards.

---

### Post by lolThisIsMyName on 2013-04-19
Hi papibe, thanks for responding! I'm using 12.10 I believe. The HD is a 128 GB Samsung 830 SSD right now, before it was a 512 mb western digital mechanical drive.

Not sure if this is relevant, but on drives where Windows is installed, it boots just fine.

---

### Post by matt_symes on 2013-04-19
Hi

Is this a bare metal install or are you trying to install in a VM ?

Are you using intel or nvidia graphics ?

Is this a 32 or 64 bit install ?

EDIT:

Try disabling VT-d in the BIOS and enable discrete graphics.

Kind regards

---

### Post by lolThisIsMyName on 2013-04-19
Hi Matt,

It's a full install, no VMs.

I've got it set to discrete and it's 64 bit.

Thanks for your response!

---

### Post by matt_symes on 2013-04-19
Hi

Disable VT-d in the BIOS and try to install again.

People have comlained about the 64bit version, your laptop model, graphics and VT-d.

Take a look:

[http://forums.lenovo.com/t5/Linux-Discussion/64-bit-Linux-W520-amp-nVidia/td-p/577789](http://forums.lenovo.com/t5/Linux-Discussion/64-bit-Linux-W520-amp-nVidia/td-p/577789)

Kind regards

---

### Post by lolThisIsMyName on 2013-04-19
Thanks, but how do I disable VT-d? I can't find it in the boot menu.

---

### Post by oldfred on 2013-04-20
Is Windows installed in UEFI mode? 
IF so you need to install Ubuntu in UEFI mode with secure boot off, but UEFI on or BIOS/Legacy off.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 


 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive

---

### Post by lolThisIsMyName on 2013-05-11
[COLOR=#000000]>Is Windows installed in UEFI mode?

No, Windows is not installed at all. I'll give what you said a try if I can figure it out.[/COLOR]

---

### Post by lolThisIsMyName on 2013-05-15
I'm having a hard time understanding what, exactly, I'm supposed to do. 

Why won't just booting in legacy mode work?

---

### Post by lolThisIsMyName on 2013-05-15
> **lolThisIsMyName said:**
> Thanks, but how do I disable VT-d? I can't find it in the boot menu.

Can anyone answer this?

---

### Post by oldfred on 2013-05-15
Did you read the thread posted. That was for 11.10 and last post said it was fixed with 12.04. I might think that is not your issue then. But sometimes there are regressions where issues reappear.

But there are a lot of Intel settings in UEFI/BIOS. Another user with a different brand UltraBook did say he had to turn off the Intel NIC or network interface controller to get it to install. It may be required later. UltraBook is Intel systems with cache and dual video with nVidia.

Review what UEFI/BIOS settings you have.

Most with the UltraBooks turn one or the other video off and then use that video driver to boot initially. With nVidia only you can use nomodeset to get into a lower quality video but it should boot.

---

### Post by lolThisIsMyName on 2013-05-16
I've tried this with 12 and 13, no dice. I've tried booting in both legacy mode and UEFI with no luck. Switching the options for the video card didn't work either. 

It seems like legacy ought to work just fine and from what I'm reading in other posts where people were using the W520 with Ubuntu (or even other distros), they didn't mention any problems.

---

### Post by oldfred on 2013-05-16
Is this after you have Ubuntu installed or still with live flash drive installer?

---

### Post by lolThisIsMyName on 2013-05-18
This is after it's been installed. The live CD boots and seems to function normally. The install process proceeds normally too, but then when it comes time to boot from the hard drive (which appears to have a full install on it), all I get is a blank screen with a blinking _ symbol.

---

### Post by lolThisIsMyName on 2013-05-18
> **oldfred said:**
> Is Windows installed in UEFI mode? 
IF so you need to install Ubuntu in UEFI mode with secure boot off, but UEFI on or BIOS/Legacy off.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 


 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive


The bootloader explanation seems pretty plausible, but unfortunately I can't find actual instructions on *how* to install something like GRUB in a secure version.

---

### Post by oldfred on 2013-05-18
If you boot in secure boot mode, and then boot Ubuntu liveCD or your installer and run Boot-Repair, check off secure boot & it should upgrade you to the signed versions of grub & kernel.

       Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)


 One user posted this which you probably need to do for those systems that only boot Windows with secure boot on:
> The key was to launch into Window 8 with secure boot enabled then choose Restart in Windows 8 selecting USB as the device to restart on. 
This is really strange since the big breakthrough was being able to run Boot Repair launched in "secure boot" mode and checking the "Secure Boot" checkbox in Boot Repair before running it.

---

### Post by lolThisIsMyName on 2013-05-19
I was just able to get Mint 15 to boot off the HD. Not sure what happened, because I didn't change any of the settings.

Thanks to everyone who offered their help.

Boot was set to UEFI/Legacy (with legacy first) and the graphics were set to discrete.

---

