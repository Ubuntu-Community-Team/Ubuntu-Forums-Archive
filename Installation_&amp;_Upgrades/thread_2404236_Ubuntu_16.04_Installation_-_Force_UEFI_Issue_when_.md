---
title: "Ubuntu 16.04 Installation - Force UEFI Issue when system and iso disk are UEFI"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by abomstar on 2018-10-21
[COLOR=#242729][FONT=Arial]Hello,

I am a new user of this forum so please let me know if I am posting this in the incorrect place. 

I am experiencing a few issues trying to install Ubuntu 16.04 LTS as a dual boot option on my Lenovo Legion Y730 laptop, but there is one in particular that I can't seem to work past. It is my first time going through with an Ubuntu install so I've been visiting many forums trying to get this working, but I have finally hit a spot where I haven't been able to find a solution.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The main issue I am currently experiencing is when I am going through with the installation setup and it gives you the option to:[/FONT][/COLOR]

[LIST=1]
[*]Download updates while installing Ubuntu.
[*]Install third-party software for graphics and WiFi hardware, flash, MP3 and other media.
[/LIST]
[COLOR=#242729][FONT=Arial]I noticed that my installion would freeze if I included the second option so I have been proceeding from this step by selecting only the first option. Once I press "Continue", I receive the following error:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][I]Force UEFI Installation? 
This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.[/I][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]*If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.*[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][ATTACH=CONFIG]281404[/ATTACH][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The issue I am having is that the only other system I have installed in the factory installed Windows 10, which I have confirmed was installed using UEFI (see picture below) and I am trying to install in UEFI mode, so I am not sure where this error is coming from. I have seen this error on other forum posts and the solution always has to do with ensuring that the BIOS mode is the same as the bootable drive mode, which I have done.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][ATTACH=CONFIG]281405[/ATTACH][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have also ensured that that my BIOS mode is set to UEFI in the UEFI settings. I have disabled secure boot and fast boot.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am using RUFUS 3.3 to create the bootable USB drive with a GPT partition scheme and an UEFI only target system (as my laptop current system was setup using UEFI). I have also tried an MBR partition scheme with a BIOS (or UEFI-CSM) Target system. Finally, I have ensured that the Ubuntu 16.04 iso image is not corrupted.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have no idea why the error above is appearing and would appreciate any help or insight that can be provided. I'm sure I am missing something small in the way that I am trying to proceed with the installation.

Thanks![/FONT][/COLOR]

---

### Post by oldfred on 2018-10-22
Installer must be seeing some left over boot files or partition(s). 

Even though you have not yet installed, this may show something. A bit easier than asking you to run multiple commands to show details of system.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If UEFI, you really want gpt partitioning. 
Most systems will install in either BIOS or UEFI from a MBR partitioned installer. But a few will only want gpt.
How you boot install media UEFI or BIOS is then how it installs.
 
Have you updated UEFI?
Many systems need that whether installing Ubuntu or not        for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 
Both Windows & Linux have updated kernels & drivers, but UEFI also needs updates. And new versions seem to be developed so regular updates may be required.
After update of UEFI, you probably have to reset the settings you change in UEFI. I have about 7 settings, some required like "Windows" or "Other" so Secure Boot is off and others are optional, so I keep a list.

If newer system, 18.04 may be better as newer kernel & drivers to support newer hardware.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also lots more general UEFI info in link below in my signature. 
 

    Companies use same UEFI for many systems. Just updates for different options. Even newer models may essentially be the same and have same issues.
Often bigger difference between AMD & Intel & issues by brand.
      
 Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)

---

