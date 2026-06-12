---
title: "Why install in UEFI mode instead of legacy (BIOS) mode?"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by dean.w.schulze on 2017-04-01
I've got a new Dell XPS 15 9560 laptop that I'm going to install Ubuntu 16.10 onto.  Ubuntu will be the host OS and I'll run Win10 as a guest OS in VirtualBox (it won't be a dual boot).

Is there a benefit to installing Ubuntu 16.10 in UEFI mode instead of legacy (BIOS) mode?  The reason I ask is because I installed Ubuntu 16.04 in UEFI mode on a new ASUS laptop recently and after a few reboots it would not boot.  It hung with some kind of error.  I couldn't figure out how to switch the firmware back to legacy mode so I had to return the latop.

The last two desktops I setup with Ubuntu had to be installed in legacy mode.  Installation failed in UEFI mode, but they both work fine after switching the firmware back to legacy mode and installing like they were BIOS machines.

I haven't looked at the firmware interface in the Dell XPS 15 yet, but I assume it has a legacy mode.  From what I've read UEFI can still be a problem for Ubuntu.  Is there some benefit that makes it worth dealing with the potential problems of UEFI, or could I bypass those potential problems without giving up anything by installing in legacy mode?

Thanks.

Dean

---

### Post by RobGoss on 2017-04-01
Hello and welcome, You stated your machine is new correct? this means you probably have** UEFI / BIOS**, with the new machine the manufactures has made it a bit harder to install any form of Linux on those machines

I don't feel UEFI does much besides make it harder to install and dual boot Windows with Ubuntu, since you are not wanting to dual boot you can install Ubuntu in **UEFI** or **Legacy ** mode, it won't make a difference. Things can get complicated when trying to set up a dual boot system because when you install Ubuntu alongside Windows, what ever mode Windows is installed Ubuntu needs to be installed in the same manner 

Example: I want to install Ubuntu alongside Windows, keep in mind Windows will always need to be installed first, if you're dual booting then Ubuntu needs to be installed second follow me so far :)

If this is a new machine then most likely Windows will be installed in **UEFI / BIOS **mode, so if you want to install Ubuntu it will have to be installed in the same way UEFI, 
[B]
**Note:**[/B] I see you want to install** Ubuntu 16.10**, this release will only be supported for a few more months until **July 2017**, if I were you I will install **16.04.2**, it will be supported for a few more years and is a much better option. You may want to keep this Ubuntu release page for future reference [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

This may help you with understanding what UEFI is and how things work [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Best of luck

---

### Post by dean.w.schulze on 2017-04-01
This laptop has a i7-7700HQ processor (Kaby Lake H) which is pretty new so I was going with the latest version of Ubuntu.  Based on the last comment here

[https://www.reddit.com/r/Ubuntu/comments/5qjq4v/dell_xps_15_kaby_lake_w_nvidia_1050_review_2017/](https://www.reddit.com/r/Ubuntu/comments/5qjq4v/dell_xps_15_kaby_lake_w_nvidia_1050_review_2017/)

16.04 works just fine on this laptop so I'll start with 16.04.2 per your suggestion.

Do you know anything about linux kernel support for this processor?  16.04.2 comes with the 4.8 kernel.  I've read that I should use CPUFreq instead of P-State, and some later kernels have that by default.  This review used kernel 4.9.5

[http://www.phoronix.com/scan.php?page=article&item=intel-7700k-linux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-7700k-linux&num=1)

If I upgrade the kernel to the 4.9 series will that work with the long term support for Ubuntu 16.04, or do I defeat the LTS by manually upgrading the kernel?

Thanks.

---

### Post by oldfred on 2017-04-01
Very, very new hardware has issues with Linux whether UEFI or BIOS. Most vendors do not create drivers for their new hardware, just for Windows. And then Linux developers have to create/modify drivers, test, add to kernel or support software. And then it gets incorporated into a distribution. 
Dell is one of the better systems as does create sputnik which normally later gets incorporated into standard Linux.
       Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/) 
    
 Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843) 


Microsoft wanted vendors not to even develop BIOS/MBR based driver for any new hardware when Windows 8 came out, but many large users/corporations still ran Windows 7 in BIOS mode but wanted to be able to upgrade hardware, so that requirement was dropped for the time being.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by RobGoss on 2017-04-01
> 
Do you know anything about linux kernel support for this processor? 16.04.2 comes with the 4.8 kernel. I've read that I should use CPUFreq instead of P-State, and some later kernels have that by default. This review used kernel 4.9.5

I would have to say try it and see how it goes, the level of support as far as kernels are concern I think are pretty good, Run the live installer and see how it goes the machine you have should do well considering it's a i7

Most of my machines are Dell and I don't have any issues what so ever installing Ubuntu or other distributions, well I did have issues with Linux lite, seems like there is not much support for AMD drivers so I just moved on to another distribution until something changes. I try to keep each distro available in order to trouble shoot issues

---

### Post by ubfan1 on 2017-04-01
You can update the kernel on LTS releases with the appropriate hardware stack packages (names have ...lts-xenial etc.), but those packages only get the support term of the distribution to which they are native.  You will need  to keep updating the hardware stacks if you start using a 9 month support one.

---

### Post by dean.w.schulze on 2017-04-03
Installation of 16.04.2 went off without a hitch.  I made two changes to the firmware before installation:  disable Secure Boot, and change the SATA property from RAID to AHCI.  I didn't attempt to change anything else in the firmware so whatever UEFI mode the firmware was using is still the same.

I gave Ubuntu the entire SSD.  It is not a dual boot so I wasn't concerned at all with what would happen to Win10 with the two firmware changes.  I run a Win10 virtual machine without any problems.

I've been running for two days now without a problem.  The SSD is fast, an external 1080p monitor was recognized automatically, and I've booted several times with no problems at all with the firmware, MBR, etc.  It boots fast and so far has never encountered an error.  I run the laptops 4k display in 1080p mode when connected to an external 1080p monitor to avoid scaling issues.

I don't have any estimates for power consumption or battery life.  I haven't had the chance to try an external 4k monitor or multiple external 1080p monitors.  If I get access to them I'll try them out and report back.

So far this Dell XPS15-9560 is running like a champ with Ubuntu 16.04.2.  Costco has it on sale in the US through April 27:

[https://www.costco.com/Dell-XPS-15-Touchscreen-Laptop---Intel-Core-i7---4K-Ultra-HD---4GB-NVIDIA-Graphics.product.100336318.html](https://www.costco.com/Dell-XPS-15-Touchscreen-Laptop---Intel-Core-i7---4K-Ultra-HD---4GB-NVIDIA-Graphics.product.100336318.html)

---

### Post by oldfred on 2017-04-03
Glad it is working.
Is it in UEFI boot mode? How you boot install media is then how it installs.

---

### Post by RobGoss on 2017-04-03
Dells run Linux really well not surprising, it's always feels good when the installation goes smoothly glad you had a good experian with the installation

---

### Post by dean.w.schulze on 2017-04-03
I installed off of a bootable USB created on Win10.  I just hit F12 at the Dell splash screen.  I think the two choices were to boot from the USB or the Windows MBR, and I selected the USB.  So I didn't explicitly select a boot mode.

Now that installation is complete is there a way to tell which mode it boots in?

---

### Post by Bashing-om on 2017-04-03
dean.w.schulze; hey;

Literally running 
```

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

```
is one way to  tell you if you're booted via UEFI.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by RobGoss on 2017-04-03
This is another way to see if the system booted in UEFi mode


```
dmesg | grep "EFI v"

 
```

If the system was booted in UEFi mode then you should see this

```
[ 0.000000] EFI v2.00 by American Megatrends
```


You can also access your BIOS and see if your settings is set to UEFI it should say something like enabled

---

