---
title: "Can't boot into Ubuntu 16.14 after install"
date: 2018-03-03
forum: Installation &amp; Upgrades
---

### Post by soylentjosh on 2018-03-03
Hello!!

I purchased a Minix N42C-4 Mini PC (Intel Apollo Lake processor) preloaded with Windows 10. I installed Ubuntu 16.04 and it appparently went smoothly. At the end of the seemingly successful install I rebooted and can't seem to get Ubuntu to load. I'm stuck at this command prompt on the screen in the attached image (my apologies for the cropped edges, that's whole other issue entirely I suppose, since its not possible to fix through the monitor's settings).

My next step was to run Boot-Repair with the recommended fixes...still no luck booting into Ubuntu. The location of the boot-repair log info is [http://paste.ubuntu.com/p/2VyPxJvGtT](http://paste.ubuntu.com/p/2VyPxJvGtT)

Can somebody help me determine what's going wrong here and how to successfully boot into Ubuntu?

Thank you very much in advance,
Josh

---

### Post by oldfred on 2018-03-03
Have you tried with UEFI Secure Boot off?
And you need to boot live installer & run Boot-Repair in UEFI mode.

Startup.nsh is an UEFI script file. Not familiar with that. Probably a default file provided by your vendor.

line 294
This live-session is not in EFI-mode.

---

### Post by soylentjosh on 2018-03-04
I have tried booting with CSM Support in the BIOS menu both enabled and disabled. Both ways I get the screen with the Startup.nsh script.

Should I try Boot-Repair again with CSM Support enabled?

Thanks
Josh

---

### Post by oldfred on 2018-03-04
Most systems CSM support means BIOS/Legacy boot.
A few need to have that on, but you still can boot in UEFI mode.

Just reviewing partitions again, I think you did install in BIOS mode, so turn on CSM support.
I originally saw a FAT32 partition which is used for UEFI boot, but that was sda.

The first part of script does not parse mmcblk drives as well, so not all info shown.

---

### Post by soylentjosh on 2018-03-04
Pardon me as I try to understand; I'm a step above beginner on Linux, but definitely at least two steps below advanced. I initially thought by toggling CSM Support between Enabled/Disabled that I was turning on/off UEFI Secure Boot mode. I'm gathering that they're related but not exactly the same. If setting the system to CSM Support Enabled isn't the exact same as booting with UEFI Secure Boot mode Disabled, do you recommend a different procedure to turn off UEFI Secure Boot in order to attempt to boot into Ubuntu?

Perhaps my misunderstanding caused me to install Ubuntu in a non-supported configuration. Do you think I should re-install?

Thanks again,
Josh

---

### Post by oldfred on 2018-03-04
New UEFI systems work with the now 35 year old BIOS/MBR configuration for backwards compatibility and with newer UEFI/gpt configuration.
How you boot install media is then how it installs. And the boot of a flash drive or DVD is separate from the boot setting of the internal drive.
Most UEFI show two settings for USB flash drive one clearly UEFI as UEFI:flash but other is just flash where flash is the name or label of the flash drive.

And most UEFI have multiple related settings.
UEFI Secure Boot on/off is often one separate setting, but some simple UEFI combine it.
And it often is not labeled Secure boot, but "Windows" and "Other". But that is the secure boot setting as fine print says to use "Other" for Windows 7 as in UEFI mode it does not support Secure Boot. 
If UEFI Secure boot is on, you may have to specifically allow USB boot as that is not secure. And if Secure Boot is off may still have to turn on the USB boot setting.
Then you have the default boot of internal drives. If Secure Boot is off, you can still select UEFI or BIOS/CSM/Legacy. 
My system has a CSM setting, and when on I then have a sub-menu that allows me to turn on UEFI boot. Seems backwards but that is how mine is configured. And each vendor does it somewhat different, so you have to look at all the UEFI screens, each setting & the info it says about those settings.

If you installed in BIOS mode, you will  need CSM  on and still may have to specify to boot in CSM/Legacy/BIOS mode.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by soylentjosh on 2018-03-14
Somehow the solution to this was re-installing with a CD through a peripheral USB DVD/CD-ROM drive rather than the Live USB stick I had attempted before. Go figure!

Thanks again for your help,
Josh

---

