---
title: "Can't boot Lubuntu 20.04 after installation"
date: 2021-05-02
forum: Installation &amp; Upgrades
---

### Post by duckwobble on 2021-05-02
Hello,

I've combed through several similar posts and tried various things which have had little effect!

My laptop is a HP ProBook 4540s. I've installed an ISO onto USB with Unetbootin.

(It took me a while to get through all the BIOS to even install it!)

The BIOS settings are UEFI hybrid, I've disabled Fast Boot and Security Keys, or whatever. I've also disabled booting from floppy and pxe, and ordered the boot sequence appropriately.

I've tried Gnome Disk Utility - to make the sda1 bootable, I also did this through the KDE Partition Manager.

Then I tried boot-repair, but it didn't give me any further instructions, except for this link:

[http://paste.ubuntu.com/p/C3jMp42K7d/](http://paste.ubuntu.com/p/C3jMp42K7d/)

I'm currently exploring GRUB - as you might guess, I'm quite new to Linux, and Lubuntu.



Any assistance would be much appreciated. Trawling through similar but different problems can be confusing!
Much gratitude,

Duckwobble

---

### Post by grahammechanical on 2021-05-02
A little bit of history. In the early days computer motherboards had an integrated circuit (chip) that held information about the hardware & boot order and all that stuff. It is called BIOS (Basic Input Output System). Then an improvement was made. BIOS was replaced with UEFI (Unified Extensible Firmware Interface). You have a UEFI motherboard. That means an operating system can be installed in EFI mode or BIOS/Legacy/CSM mode. CSM = Compatible Support Module.

With UEFI motherboards we can run the Ubuntu installer ISO in either UEFI mode or BIOS/Legacy mode. Whichever mode we load the Ubuntu installer in that is the mode Ubuntu will be installed in.

To quote Boot Repair

> This live-session is not in EFI-mode.

To quote you

> The BIOS settings are UEFI hybrid,

Lubuntu is installed in BIOS/Legacy mode but the motherboard is running UEFI hybrid. The two modes are incompatible.

You have two options. 1) Enter the UEFI setting utility and change the setting from UEFI hybrid to BIOS/CSM/Legacy. 2) Keep the UEFI setting as UEFI hybrid or as UEFI and then re-install. Run the Ubuntu installer in UEFI mode. Let it format sda as GPT and install Ubuntu. This is the better option. In this way Ubuntu/Lubuntu will be installed in UEFI mode matching the setting in the UEFI. And the new OS should boot.

Regards

---

### Post by duckwobble on 2021-05-02
Hehe, thank you for the little lesson! 

I am pretty sure I'm loading in UEFI hybrid - with CSM. I've reinstalled it since booting in UEFI, but I did also try installing it in Legacy. It's all been quite confusing and messy!

In all attempts it hasn't booted. It is installed as sda though, rather than GPT.

The way in which I've been installing it, is loading the usb drive from the BIOS menu which boots the live OS, and then I click the Install icon on the desktop. 

The only other option is to do the OEM install?

Thank you for your help!

---

### Post by duckwobble on 2021-05-02
I did see one more option - to load it with EFI (from the BIOS menu) but the one reference I found to this in other forums didn't work.

---

### Post by duckwobble on 2021-05-02
I just ran the BIOS F10, and UEFI is definitely selected, and it's been reinstalled since I last switched it.

---

### Post by duckwobble on 2021-05-03
Running in Legacy mode:
[https://paste.ubuntu.com/p/W5DPCMByjp/](https://paste.ubuntu.com/p/W5DPCMByjp/)

---

### Post by duckwobble on 2021-05-03
Ok, so.... I'm flummoxed. I think maybe I need to manually create a /boot partition. And maybe an LVM to host it? 

Calamares/the installer doesn't like my partitioning attempts. Not sure where to go from here.

---

### Post by duckwobble on 2021-05-03
I'm also flummoxed as to why I'm in UEFI mode but the boot-repair says I'm not.

---

### Post by GhX6GZMB on 2021-05-03
How do you partition your disk during installation?

---

### Post by oldfred on 2021-05-03
Both reports show grub installed correctly to MBR for BIOS boot.
You just need to confirm your UEFI/BIOS is set for BIOS/CSM boot.

My motherboard (Asus) would only boot in UEFI mode with UEFI only. It has a UEFI or BIOS boot mode, but any attempt to boot in UEFI mode with the dual option only tried to boot in BIOS mode. Since UEFI install, it failed.
So better to have CSM or BIOS only boot mode, since install is BIOS.

---

### Post by duckwobble on 2021-05-03
Answer to partitions: initially, I just did the 'erase disk' install. Have since used gparted and attempted to write a /boot partition, but that didn't work either.

Possibly because of the BIOS install. I have attempted to install it in both BIOS (legacy?) and UEFI - so I presumed each time I installed it, it had overwritten the previous install?

I think UEFI would be preferable for my motherboard, but presuming you mean legacy with the BIOS - I have selected legacy mode and it still fails to boot.

---

### Post by oldfred on 2021-05-03
Did you change from last Boot-Repair report?

You want either UEFI with gpt partitioning.
Or BIOS/CSM/Legacy. And you can use MBR or gpt, but gpt then requires a 1MB unformatted partition with bios_grub flag for BIOS version of grub.

But whichever mode you want or initially select, you have to be consistent and always boot in that mode.

---

### Post by duckwobble on 2021-05-04
Aha. Didn't know about the bios_grub partition..!

I did install again, on uefi with csm, after attempting to manually partition the drive on gparted (gpt), but I couldnt mount them on gparted, nor on the installer, so I allocated another partition for the installation. Partitions are something I have very little experience of - I thought if I used the 'erase disk' option it would wipe the partitions I'd made? I did try and make sense of various guides...! None of them mentioned bios_grub.

I have since updated the firmware on my ssd but I don't know if that's relevant. 

You're the second person to include csm in the bios vs. uefi, and I'm wondering if the problem hinges on me booting in uefi with csm?

I've tried without csm, but usb isn't available in the list of manual boot options. All I can do there is enter an efi filename. I've tried searching for one without much luck.

---

### Post by duckwobble on 2021-05-04
I've managed to clear another usb, and I'm going to try and work through that guide you posted yesterday, or try a different OS, or something!

---

### Post by duckwobble on 2021-05-04
I feel like I've jumped in the deep end a little bit here, and overwhelm myself with all the potential answers in the many forums. Just need to slow down and figure it out. 

At least I've got a spare usb now to experiment with, and I can do what I need the laptop for with live boot. There's just that little niggle that it's still broken...! 

Windows crashed, so it's just this new ssd and a live linux now &#128517;

---

### Post by oldfred on 2021-05-04
I do recommend gpt over the 40 year old MBR.
I converted my first drive to gpt in 2011 for Ubuntu with XP on a separate MBR drive. Then found I had to have the bios_grub partition for grub to install correctly.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

You can also use gparted to partition in advance, but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Depending on size of external drive 100 to 500MB for ESP, 1 or 2MB for bios_grub and if not large just one ext4 partition for / (root). If larger drive then  30GB or more for / and rest for /home and/or data partition(s).
It now defaults to swap file if no swap partition found. Some still suggest swap partition including Linus.

---

