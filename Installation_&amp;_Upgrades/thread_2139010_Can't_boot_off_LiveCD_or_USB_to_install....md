---
title: "Can't boot off LiveCD or USB to install..."
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by ThePhantom0114 on 2013-04-25
So I just recently built a new computer and I have Windows 8 running on it, bios is set to UEFI, and Secure Boot is off. Windows 8 runs perfectly on it. Well with the new version of Ubuntu out, I thought I would give it a try in a dual boot on my new system. I have a separate hard drive just for Ubuntu, however I can't even get an installer to load to let me install it! I have tried 13.04 and 12.10 on CD and 13.04 on USB, all x64 versions, and when I boot the PC, it sees the device, shows it as UEFI, I choose it and get the grub menu to choose Try Ubuntu, Install Ubuntu, etc, no matter what a I pick, it doesnt work. On the CDs, no matter what I pick, the screen just goes black and it sits there. I'm wondering if I wait long enough, it might do the same thing the USB does, not sure, usually only waited 5-10 minutes. For USB version, I choose either Install or Try, it goes black for about a minute, then I get the Ubuntu loading screen, it goes for about 30 seconds, and then I get a bunch of SQUASHFS Errors about things not being readable. I can take the same ISO and load it in VirtualBox and install it just fine, but not on my PC. I also tried 2 different flash drives in case that was the issue. Any suggestions?

---

### Post by oldfred on 2013-04-26
Some others with two drives. I think you need to partition in advance with gpt or else the installer will not add an efi partition at the beginning of the drive. It may not get used, but you may want it later to make each drive independent. 
       I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

    

 Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)


 You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

You may have video issues. What video card/chip do you have? Is it an Ultrabook or dual video system. If so you may have to turn one off in BIOS.
If nVidia you may need nomodeset on grub UEFI boot line. It is different than all the BIOS boot screens and is a standard grub menu. To add nomodeset use e and scroll down to the linux line, replace splash quiet with nomodeset. Some system require other boot parameters and or other video paramaters.

      
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by ThePhantom0114 on 2013-04-26
Thanks for the great response, and I will definitely use a lot of that information when I get to the install process, however I can't get the installer to even start... No matter what media I use, once I click the Try Ubuntu or Install option, the screen either goes black or it starts to load and then gives a SQUASHFS Error (well...a whole lot of these errors) and freezes. I've never had issues launching the installer before, so I'm guessing its something to do with booting in UEFI mode. Can anyone think of anything that might cause the installer to fail to start at all? I have an AMD 7950, but could there be some line required in Grub for that? I've never needed a special line like that before for AMD, but this is the first time I have tried installing linux with this new video card, so I guess thats possible, however when I use the USB drive, I get video, it just fails with the SQUASHFS Errors... Any other possible boot parameters needed?

---

### Post by siepo on 2013-04-26
Maybe you have better luck with another image, e.g. a text-mode server install. You can always add your preferred desktop afterwards.

List of images:
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

---

### Post by oldfred on 2013-04-26
I do not pay close attention to AMD as I have nVidia.

I think there was some issue originally with the very new AMD 7000 series, so probably best to use newest version or 13.04 64 bit.

This is old but I think some had to use generic to force the generic driver, until correct proprietary driver is installed.

 Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1 
[*]nVidia: nomodeset 
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

This was with 12.10
       [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_amdstock&num=1)
On the proprietary driver side, the AMD Catalyst 12.11 Beta Linux graphics driver was used. For this initial testing, three discrete graphics cards from the AMD Radeon HD 5000/6000 series were used, since pre-HD5000 graphics cards are now on the Catalyst Legacy driver and the latest-generation Radeon HD 7000 series hardware still doesn't fully work with the open-source Gallium3D "RadeonSI" driver.

---

