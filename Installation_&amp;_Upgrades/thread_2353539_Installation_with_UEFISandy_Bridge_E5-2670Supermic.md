---
title: "Installation with UEFI/Sandy Bridge E5-2670/Supermicro X9Dai Kernel Panic"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by mike0810 on 2017-02-22
Hello,

i can not install 16.04 and 16.10 on my Rig. The System is Supermicro X9Dai with Bios 3.2 in UEFI Mode, 96GB Ram, Two Sandy Bridge E5-2670 in Hyperthread Mode. I tried also to reduce the cores to 1 or 2 in Bios.

I prepared the Boot USB Stick with Rufus: 
1. Downloaded the ISO
2. Used GPT for UEFI
3. Used Fat32 as File System
4. Wrote the IOS in ISO Mode, not DD. 

The System Boots from the USB Stick until I get a Kernel Panic (I get a Kernel Panic with Fedora too).
Kernel panic - not syncing: stack-protector: Kernel stack is corrupted in: fffffsomeaddress

I attach the Call Trace as attachment.

I did not find anything comparable with google.[ATTACH=CONFIG]273845[/ATTACH][ATTACH=CONFIG]273846[/ATTACH]

Thanks for help, 

Michael

---

### Post by DuckHook on 2017-02-22
> **mike0810 said:**
> …Used Fat32 as File System…Welcome to the forums, mike0810

No Linux distro, including any of the 'buntus, will work on a fat32 filesystem. That is such a primitive (frankly, awful) filesystem, that it is simply missing the elements that Linux needs to operate. It's like trying to build a car on top of a skateboard. Even Windows will not install on fat32 and that filesystem is native to Microsoft.

Tell us more about what your end goal is. Are you dual booting with Windows? If this is a single-boot Linux-only system, then let the installer repartition your whole disk and install the right filesystem (ext4) by choosing "Use whole disk" during the partitioning phase. The right filesystem will be installed automatically.

You should also try running a session on the LiveUSB/DVD prior to actually installing. If the LiveUSB works, then you know that you don't have an actual HW incompatibility.

---

### Post by DuckHook on 2017-02-22
Apologies.

Totally misread your post. You are using FAT32 on your USB stick. OK. No problem with doing that.

It's the LiveUSB that is causing you grief.

[LIST=1]
[*]Did you checksum the downloaded image?
[*]Does it, in fact, boot as a LiveUSB into "Try Ubuntu"? (Don't try to install anything.)
[*]Have you tried a different USB port?
[*]Have you tried a different USB stick?
[*]Are you dual booting? If so, does Windows work on your machine?
[*]Can you run memtest at boot?
[*]Do you have both fastboot and secureboot turned off in BIOS?
[/LIST]
There are other things to try, but first the above.

---

### Post by oldfred on 2017-02-22
What video card are you using?
If nVidia or AMD, you may need nomodeset and possibly other boot parameters.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

Older Xeon thread:
[https://ubuntuforums.org/showthread.php?t=2277028](https://ubuntuforums.org/showthread.php?t=2277028)
[https://ubuntuforums.org/showthread.php?t=2259883&page=2](https://ubuntuforums.org/showthread.php?t=2259883&page=2)
> So the problem was the aic79xx SCSI controller - once the device is enabled in the BIOS, then the kernel boots fine.

---

### Post by mike0810 on 2017-02-23
I forgot to mention, there is an Areca Arc-1320iX in the System. I took a look to the call trace and libsas popped up many times. So decided to remove it and boot went fine. Now have to figure out how to enable the areca after installation.

---

### Post by mike0810 on 2017-02-23
The Problem was the ARECA ARC-1320 SAS Controller. The Solution to the problem is in fact written in the Driver Installation Readme of the Areca Controller.

I attach the Readme here for everyone with the same problem.

But only to get to boot, just add

modprobe.blacklist=mvsas 

to the Kernel Parameter in the Boot Menu of the Live CD or the Installer.

All details for installing the Areca Pre or Postinstall are in the Readme and in the Driver Package from the Areca Homepage.

Thanks all!

---

### Post by DuckHook on 2017-02-23
Glad you found the solution, and appreciate you posting it for the benefit of the community.

Good Luck and Happy Ubuntu-ing!

---

