---
title: "Ubuntu 22.04 LTS amd64 Bootable USB Black Screen"
date: 2022-06-13
forum: Installation &amp; Upgrades
---

### Post by 0utphase on 2022-06-13
Greetings,


I'm attempting to install Ubuntu 20.04 LTS amd64 iso with a USB bootable drive. I'm able to reach the GRUB menu to make a selection. Once I select 'Try or Install Ubuntu' or 'Ubuntu (safe graphics)' options, the screen will go black, even after some time.


My best guess is that my graphics card is causing the problem, although I have attempted the safe graphics option that adds nodemodeset to the first option.


balenaEtcher was used to create the Bootable USB stick per the installation instructions. I've also used Rufus using ISO and DD mode with default settings.


I'm running an ASUS GL12CX motherboard with an American Megatrends GL12CX.313 SMBIOS, in UEFI mode. Fast Boot and Secure Boot are disabled. My graphics card is a NVIDIA GeForce ASUS RTX 2080 Turbo.


I haven't been able to get to an installation window on this machine. Loading the sticks on a 2011 Mac Mini has no problem getting to the installation stage.


I'm not sure if the command line in GRUB should read the following paths, I've included them just in case.


GNU GRUB version 2.06


For 'Try and Install Ubuntu' the commands read:


setparams 'Try or Install Ubuntu'


	set gfxpayload=keep
	linux		/casper/vmlinuz	file=/cdrom/pressed/ubuntu.seed maybe-ubiquity quiet splash ---
	init rd	/casper/initrd


For 'Ubuntu (safe graphics)' the commands read:


setparams 'Ubuntu (safe graphics)'


	set gfxpayload=keep
	linux		/casper/vmlinuz	nomodeset file=/cdrom/pressed/ubuntu.seed maybe-ubiquity quiet splash ---
	init rd	/casper/initrd


For 'OEM install (for manufacturers)'


setparams 'OEM install (for manufacturers)'


	set gfxpayload=keep
	linux		/casper/vmlinuz	file=/cdrom/pressed/ubuntu.seed only-ubiquity oem-conbfig/enable-true quiet splash ---
	init rd	/casper/initrd


I've used both a DisplayPort and an HDMI port available on the GPU.


Any recommendations are appreciated or if more information is needed, please reply and I will provide what I can. Thanks.

---

### Post by oldfred on 2022-06-13
I have seen a variety of Asus need both UEFI firmware & SSD firmware updates to work.

Not sure how similar these may be, those with same chip AMD or Intel will be closer to same:
Asus ROG Strix G17 Intel Core i7-10750H Nvidia
[https://askubuntu.com/questions/1279496/hard-time-installing-ubuntu-20-04-as-dual-boot-on-asus-rox-strix-g17](https://askubuntu.com/questions/1279496/hard-time-installing-ubuntu-20-04-as-dual-boot-on-asus-rox-strix-g17)
Asus ROG Zephyrus GA502 Ryzen 7 3750H + Nvidia GTX 1660 Ti Set up Guide
[https://ubuntuforums.org/showthread.php?t=2440670](https://ubuntuforums.org/showthread.php?t=2440670)
Asus ROG Zephyrus G Ryzen 7 GTX 1660 Ti UEFI update required, nVidia driver required
[https://ubuntuforums.org/showthread.php?t=2420199](https://ubuntuforums.org/showthread.php?t=2420199)
Asus Zenbook UX433FN with nVidia
[https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn](https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn)
Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)

---

### Post by 0utphase on 2022-06-16
Hi oldfred,

I appreciate the post. I've tried some of the following methods, including BootRepair. 

It seems that any Linux based boot has a problem with my graphics card and motherboard. Is editing the kernel for my specific machine the appropriate procedure? I've downloaded a copy of the 5.18.4 Kernel to learn more about it. I will continue to research and post any updates. Thanks.

---

### Post by oldfred on 2022-06-16
It is better to use a ppa for new kernel. 
I have not done that, but here are links.

Ubuntu 22.04 LTS is planning to use the Linux 5.15 kernel as its default, if Alder Lake CPU you may want newer kernel
[https://www.phoronix.com/scan.php?page=article&item=ubuntu-2204-alderlake&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-2204-alderlake&num=1)
> The kernel upgrades were obtained from the Ubuntu Mainline Kernel PPA

[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/](https://ubuntuhandbook.org/index.php/2020/08/mainline-install-latest-kernel-ubuntu-linux-mint/)

---

