---
title: "ubuntu 14.04 installation stuck at boot logo"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by djayzen97 on 2014-06-24
Hi, first let me say that I am very familliar with UNIX and I am far from being a noob, I program in SHELL and Objective-C and I'm not afraid of the terminal.

I have a Dell Inspiron 580, currently running windows 7. I have used ubuntu in the past and really loved it on my previous pc. I saw that it is possible to run recent games with wine and playonlinux, so I want to use linux.

I have used imgburn to make my bootable cd (I used this software to make windows cds and linux cds in the past without problems). 

When I boot from the 14.04 ubuntu cd, it simply get stuck at the ubuntu logo, I have waited 45 min without any success. I tried 12.04 wich booted but wifi didn't worked, and I would prefer to use the latest release.

Dell inspiron 580
CPU: Intel I3 530
GPU: ATI Radeon HD 4870 1GB
MOBO: dunno, the stock one included
RAM: 6GB DDR3
BIOS: Latest revision, A07 I think
WIFI Adapter: Ralink RT5370 Chipset 150Mbps Mini Wireless USB Adapter (SL-1507N)
The bios uses factory settings, aside from sata mode wich I switched from ata to ahci for better performances, I have used ubuntu with ahci on other computers without any problems.

Please let me know if you need more informations.

---

### Post by Bashing-om on 2014-06-24
djayzen97; Hi ! Welcome to the forum .

Let's get the small details out of the way first.

You did verify the .iso integrity, yes ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

Regrettable, but ATI no longer supports your graphics card, are you attempting to install with "install updates" during the install process ? Such that maybe you are freezing up trying to install a non-existent driver ??? .. 
In this instance try and boot the liveUSB; As soon as the bios screen clears, depress and hold the right shift key -> language screen; escape key to accept the default -> boot options screen. Choose " check disk for defects". When the check completes you will be directed to reboot. Reboot back to the boot options screen and select "try ubuntu". Can you now boot to the desk top in this trial mode ?

Else try this:
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s) -space or enter to accept and then the escape key to exit-; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top.

What ever it may take to boot in the liveUSB, will require replicating in the installation .


[INDENT][INDENT][INDENT]Hope This Helps
[/INDENT][/INDENT][/INDENT]

---

### Post by djayzen97 on 2014-06-24
Thank you.

My cd is correct as I used it with multiple computers :)

As for the GPU, it works with the community radeonDriver wich is by default in the kernel.

I cannot access the setup installation with the 14.04 cd, what it does is after the BIOS screen, it would show ubuntu logo and get stuck on that forever. I only got 12.04 to boot to the setup and live cd session, but wifi wouln'd connect to my network and I would prefer 14.04 rather than 12.04.

The kernel argument at boot time you suggested is some sort of graphic compatibility right ? I will try that when I get home in the next hours.

---

### Post by Bashing-om on 2014-06-24
djayzen97; Hey hey,

All to the good.

We just have to see what it will take to boot you up in release 14.04 in the "try ubuntu" mode.
We focus on that and then the actual install should be smooth as silk.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by djayzen97 on 2014-06-24
Integrity checking haven't detected any errors.

Very weird, holding the up arrow key booted into verbose mode and worked (I tried a couple of minutes ago without success).

I am on the desktop... I will try to install and see if it boot correctly.

---

### Post by oldfred on 2014-06-24
Nomodeset is the most often used kernel parameter, and that works for my nVidia card. With AMD it may work or may need different parameter.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

These are older settings, try each of these if nomodeset does not work:

 

[LIST]
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]

---

