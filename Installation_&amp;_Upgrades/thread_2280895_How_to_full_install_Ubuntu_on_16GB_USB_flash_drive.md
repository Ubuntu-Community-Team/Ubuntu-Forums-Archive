---
title: "How to full install Ubuntu on 16GB USB flash drive with multiple boot option!?"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by firefox1234 on 2015-06-03
Hello! ;)

I read many post about ubuntu installation on USB flash drive but not found my install plan!

I have a USB flash drive, **ADATA UE700 UFD**, **32GB**, **USB3** and want to install Ubuntu on it to work on public computers when my laptop is not near me.

I want Ubuntu on my flash drive [COLOR=#ff0000]1)[/COLOR] being **updated**/upgraded (Although I perfer **LTS** versions).
[COLOR=#ff0000]2)[/COLOR] Detect hardwares on public computers (**At least** to connect to the **Internet**).
[COLOR=#ff0000]3)[/COLOR] Works on **UEFI** and **Legacy** booting systems (Seems **Avira Rescue System** does it).
[COLOR=#ff0000]4)[/COLOR] Access to **ExFAT** partition on USB flash drive (I need/must add a ExFAT partition with 16GB space besides Linux partition (**ext4**) for works on Macintosh and Windows for regular usage).
[COLOR=#ff0000]5)[/COLOR] Works on **64-bit** and also **32-bit** systems (Seems **Avira Rescue System** does it).

With these conditions what is your recommended install plan? [COLOR=#ff0000]1)[/COLOR] **LiveCD with Persistence**, [COLOR=#ff0000]2)[/COLOR] **Full installation**, [COLOR=#ff0000]3)[/COLOR] **Minimal installation** [COLOR=#ff0000]4)[/COLOR]** LiveCDCustomizationFromScratch** or **other options**

Kind regards
  -- firefox1234

---

### Post by grahammechanical on 2015-06-03
Item 5) Install a 32 bit OS because a 64 bit OS will only run on a 64 bit CPU. Whereas, Ubuntu 32 bit will run on both 32 bit and 64 bit CPUs.

I think that you will find that the difference between UEFI and BIOS boot is applicable when we are installing Ubuntu. If the existing OS is installed in EFI mode, then Ubuntu has to be installed in EFI mode and that means the USB has to be loaded in EFI mode. If the existing OS is installed in Legacy mode then Ubuntu must be installed in Legacy mode.

The issue that you may come up against is Secure Boot. If the machine has secured boot enabled then you need Ubuntu to have a signed kernel that meets the secure boot specification. Creating a live Ubuntu USB memory stick with persistence will have both a signed kernel and an unsigned kernel. Otherwise we could not use a Live USB memory stick to install Ubuntu with secure boot enabled on the intended machine.

I am not sure if we will get a signed Linux kernel if we full install Ubuntu on a USB memory stick. I am also not sure the Ubuntu 32 bit will come with a signed kernel.

There are inherent contradictions in your specification. You may have greater success if you have two USB sticks. One for 32 bit machines and BIOS motherboards and one for newer machines with UEFI and secure boot and 64 bit CPUs.

By the way, do not install any proprietary video drivers on the OS on the USB stick. And you may find that it will also lack some drivers for certain WiFi adapters. A proprietary driver would be needed and you have no way of knowing what WiFI hardware you are going to come up against.

Regards.

---

### Post by firefox1234 on 2015-06-03
Thanks Graham!
So recommended ISO file is 32-bit that works on most PCs!?

**Full installation** will be better or Live USB with **Persistence**?
Currently I using Puppy Linux as Live USB with Persistence on 2GB USB flash drive.

---

### Post by oldfred on 2015-06-03
Only recently have some capabilities for 32 bit UEFI boot been enabled.  Best to use 64 bit if you want UEFI.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)
Live session failed to start from USB with persistence enabled
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1239833](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1239833)

This can be done, but grub seems to get out of sync on one version update or the other and then it stops working.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by sudodus on 2015-06-04
It will be hard to get a system that satisfies the whole specification.


A. If you want a system that works with 32-bit processors and 64-bit processors, and in BIOS mode and UEFI mode I suggest that you try according to the following link
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]                 

You can add a partition with the label casper-rw for persistence.


B. If you would be happy with two pendrives, you have many more options.

B1. You can rather easily install a 32-bit system for all PC computers that run in BIOS mode (a 'normal' installation, but to a USB pendrive instead of to the internal drive),

B2. You can install a system for PC computers in UEFI mode. It *should* survive updates and upgrades, at least if it is disconnected when Windows is running. But I have seen problems ...

B2.1. Either you do it yourself (a 'normal' installation, but to a USB pendrive instead of to the internal drive),

B2.2. or try according to the following link, but that system works only in 64-bit computers,

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506")
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
[/URL]

---

### Post by amjjawad on 2015-06-09
Hi,

It seems like you want to do many things at the same time and that's reminding me of myself 5 years ago, when I first entered the Open Great World of GNU/Linux :)

If I were you, I'd give [**ToriOS**]("http://torios.net/") a go.

I'd be very interested to see how that would be helpful. I haven't played yet with ToriOS on USB Drives yet but something is telling me that it could be the best option for you.

Why am I recommending ToriOS?
Because it does work on NON-PAE and PAE machines as well.

If the OS is built for 64-bit machines, it will not work on 32-bit machines.
If the OS is built for 32-bit machines, it can work on 64-bit machines but can't read the whole RAM if it is above 4GB.

I think you're at the stage of 'trying' what is the best and what is not. Thus, I am sharing this suggestion with you :)

I see you're surrounded by experts over there and my input would be the less important compared to them because by the time I was busy with my projects, they were and still helping countless people so I am sure you'll find what you are looking for :D

ToriOS can be used as a LiveCD/LiveUSB (less than 700MB) and can be installed a disk. The choice is yours ;)

Hope that helps!

---

### Post by mastablasta on 2015-06-09
> **firefox1234 said:**
> 
[COLOR=#ff0000]3)[/COLOR] Works on **UEFI** and **Legacy** booting systems (Seems **Avira Rescue System** does it).
[COLOR=#ff0000]5)[/COLOR] Works on **64-bit** and also **32-bit** systems (Seems **Avira Rescue System** does it).


Avira is live OS. it boots and doesn't mount drives. it then downloads new virus definitions and scans and other things.

I think in your case you would be best off with live OS. I am not sure why you would need persistence, but I guess if you need more apps it would come in handy to install those.
you can use Yumi or something like that to install multiple distros in te 16GB space. why? well sometimes Ubutnu doesn't work but lubuntu does as well as you can add rescue distros on.

---

### Post by m6rshmallow on 2015-08-24
Thank you **amjjawad**, **ToriOS** :KS works **fine** on my **UFD**. I install it on my UFD with updated ClamAV ;)

---

