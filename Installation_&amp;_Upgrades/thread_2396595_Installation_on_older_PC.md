---
title: "Installation on older PC"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by frosty.the.snowman on 2018-07-18
Hello there,


I have:


[LIST]
[*]2011 Laptop with BIOS that has a UEFI on/off mode
[*]Windows 7 Ultimate, BIOS installed on that laptop
[*]Bootable Ubunut 16.02 USB stick with GRUB 2.02.
[/LIST]


I want:


[LIST]
[*]Dual boot, or some semblance
[/LIST]


Behavior:


[LIST]
[*]Regardless of whether UEFI is on/off, win 7 will boot
[*]If UEFI is off, the USB GRUB will not launch. I can set the boot order for the USB stick first, in which case it automatically enters "try without installing mode"
[*]If UEFI is on, USB GRUB works.
[*]Right, with UEFI on, I tried installing Ubuntu locally, only to be greeted with the following during install:
[/LIST]


*"This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.*

*If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here."*


[LIST]
[*]Deciding not to risk it, I turned off UEFI mode, and installed Ubuntu separately with a /, /boot, /home, swap. Trouble is, without UEFI, GRUB doesn't load. And apparently windows loader doesn't go for a  multi OS boot menu.
[/LIST]


Approaches I'm considering:


[LIST=1]
[*](Preferred) Installing Ubuntu with UEFI mode on, despite the warning. My thinking is this:  If UEFI mode is enabled, GRUB will load, and I can boot in Ubuntu, but GRUB won't see Windows. If UEFI mode is off, I can boot directly in Windows.
[*](Non-preferred)Install Ubuntu in some sort of legacy mode, and somehow dual boot based on this(maybe with a separate boot loader?). I have no idea how to do this.
[/LIST]


Nota Bene:

Good or bad, my windows install works, and it is set up exactly how I want it, doing the things I want, and I use it daily. Screwing around(e.g. upgrading it to UEFI) or getting rid of it is not an option. I am merely trying to expand my horizons and do some machine learning. 

So, suggestions? Will approach 1 work? If not, any way for approach 2?

Many thanks in advance!

---

### Post by oldfred on 2018-07-18
Windows requires MBR partitioning for BIOS boot.
Windows requires gpt partitioning for UEFI boot.
And UEFI highly recommends gpt for UEFI.
So if you force standard install of Ubuntu in UEFI mode, it probably will convert drive to gpt and erase it.
Better to just install Ubuntu in BIOS mode or install to another drive, if possible.

With BIOS boot mode, grub will be in the MBR and offer to boot Windows. UEFI & BIOS are not compatible, so grub only boots other systems in same boot mode. And grub only boots working Windows. So have Windows repair disk & keep Ubuntu live installer. You may occasionally need to directly boot Windows to run chkdsk or make other repairs when grub fails to boot a broken Windows.

Windows 7 can be installed in UEFI boot mode. But not easy to convert a BIOS install to UEFI. How you boot install media is then how it installs for both Windows & Ubuntu. Windows 7 DVD is BIOS only, but if copied to flash drive and a couple of files renamed it will boot in UEFI mode.

Do not use 16.04.2. Use either 16.04.1 or newest 16.04 or 18.04. The versions starting with 16.04.2  are short term versions that have to be upgraded as each new kernel is released and is intended for the LTS version to support newer systems that need newer kernels. Details:
       [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack) 
    
Do not use separate /boot. You only need / if smaller Ubuntu space or / & /home if more space allocated. Versions after 17.04 use swapfile in place of swap partition.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by frosty.the.snowman on 2018-07-18
Based on what you're saying, in my case it's best if I install Ubuntu as a BIOS install. 
I've tried to do this on the same drive(different partition, mind you) and disable the UEFI mode. 
Yet when I do this and start up my computer, it automatically launches in Windows. No windows menu selection, no GRUB, nothing.

So then, situation turns into this:
 I have a windows 7 Ultimate installed as BIOS. 
How do I install an Ubuntu on BIOS so that I can dual boot? 
What Ubuntu version should I use? 
Can I use a different partition on the same drive, or do I have to use a different hard drive altogether? 

Thanks in advance.

---

### Post by oldfred on 2018-07-18
You should be able to use another partition on same drive.
Use Windows to shrink the NTFS partition to make room. Re-boot immediately so it can run chkdsk.
You can partition in advance with gparted or partition during install. But if you want more than default partitions of / and swap(if 16.04) you must use Something Else.

It probably is a UEFI/BIOS setting. Most UEFI has UEFI Secure boot which must be off. Since you have Windows 7 UEFI Secure boot is off as Windows 7 does not support UEFI Secure Boot. But UEFI also has another setting to allow full USB access or USB boot or similar setting(s).
You then should be able to use UEFI boot menu, often f10 or f12 depending on your system. USB is not normally first in boot order, so default boot without selecting will go to hard drive. It should show to USB boot entries. One UEFI:flash and other just flash (which is the BIOS boot) where flash is name, brand, or label of your flash drive.

Also some systems, for whatever reason, work on one USB port but not on others. You may have to experiment.

---

### Post by frosty.the.snowman on 2018-07-19
I've managed to install Ubuntu on a separate partition using something else and a disabled UEFI mode. 
Sadly, I can't seem to get Ubuntu to boot. Without UEFI mode, there is no way to access GRUB, or any other menu which might allow launching Ubuntu. 
Any suggestions at this point are welcome.

---

### Post by oldfred on 2018-07-19
What brand/model system? Some need work arounds or settings.
What video card/chip? Some need boot parameters.
Have you updated UEFI/BIOS to latest version from vendor.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

