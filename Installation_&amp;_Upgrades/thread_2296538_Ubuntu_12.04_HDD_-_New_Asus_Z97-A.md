---
title: "Ubuntu 12.04 HDD - New Asus Z97-A"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by suprleg on 2015-09-26
I'm preparing to upgrade an old Folding at Home server running Ubuntu 12.04 on an sata HDD. I'll be installing a new Asus Z97-A mobo and a new i7 4790. The HDD  I want to keep in the new system boots in  "Legacy boot on HDD". I'm wondering if I'll encounter problems with my  initial boot of the upgraded system and if so what they may be. Has  anyone attempted this successfully? Off the cuff I'd assume the default  UEFI will need  to be changed to Legacy. I don't want to upgrade the  Ubuntu install or use a different drive because the stats reporting  scripts for our Team are very old, touchy, and complex so if I could  make the drive play nice with the motherboard and CPU it would save  countless hours of re-doing scripts and downtime not folding. Any  insights would be appreciated.
The HDD is currently installed on a Asus P5Q.

---

### Post by oldfred on 2015-09-26
I have an Asus X97-AR which uses the same UEFI for updates ( I have 2501). It just has different video out ports.

I wanted UEFI and default settings and only wanted to boot installer in UEFI mode. And every time I updated UEFI from Asus it reset to defaults. It is nice that it outputs changes to UEFI and you need to write them down or take the screen shot so you know what changes your have made.

I changed os type to Other, I think the Windows setting may be secure boot. But in BIOS mode there is no secure boot.
I change fast boot to normal so I have time to get into UEFI to make changes. And on reboot set to 3 sec delay for same reason.
I changed USB from partial to full and Legacy USB boot from auto to enabled
Network boot to ignore as I will never use it and no need to go off to network searching for something it will not find.
I did set Boot storage devices to UEFI only, you may not want that.
I do not change any timings or attempt to overclock. 

What video do you now have, and what are you using in new system? You may need to remove old drivers & install new, or add boot parameters. Internal video may need the newest Ubuntu version of ppa to update as Intel has made major changes to support the 4790, but those are only in newest kernel, support software & video drivers with Ubuntu. 
I used an older nVidia card 620GT and that just worked, but that was more because I actually got the wrong Asus card. Video ports out, do not match my video in on monitor. So needed nVidia card and nomodeset to boot.

I have installed and use 14.04 as main working install, but have installed all the newer versions and they work. Do not know about 12.04?

---

### Post by suprleg on 2015-09-26
Hey oldfred, thanks for responding. :-). My video card is a discrete GeForce GTX 550 Ti running fairly new "pure" Nvidia drivers. 340.46. Hardware in new system will be: Asus Z97-A, i7 4790K, G.Skill Ripjaws X Series 8GB, Corsair CX750M.
I probably should have been more complete, current Ubuntu version is: 12.04.5 LTS.

---

### Post by oldfred on 2015-09-26
What I do not know is if that new of processor will have any kernel issues.
I have 14.04, but even though it says 14.04.3 I have not updated kernel.
Linux trusy-ar 3.13.0-63-generic

Is your kernel in 12.04.5 the same? If so then I would expect it to work.

---

### Post by suprleg on 2015-09-27
The current kernel is: 3.8.0-44-generic, perhaps I'll update it before tearing the machine apart.

---

### Post by suprleg on 2015-09-28
I upgraded the kernel to 3.13.0-63-generic, I'll let people know if updating the kernel from 3.8 series to 3.13 solves potential hardware issues using the older 12.04.5 LTS release. I was sure there would be Nvidia driver issues upon reboot, but was pleasantly surprised the machine booted right into X with no apparent problems.

---

### Post by suprleg on 2015-10-03
For anyone interested, I did a final kernel upgrade just prior to tearing the computer down, 3.13.0-65-generic on a 64 bit 12.04.5 system. Happily all the new hardware is running well with no error messages. Maybe this wil help someone. 
Cheers

---

### Post by oldfred on 2015-10-03
Glad you got it working. :)

---

