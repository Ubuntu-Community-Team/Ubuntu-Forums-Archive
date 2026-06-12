---
title: "EFI/Legacy-Bios Grub2 issue"
date: 2014-10-12
forum: Installation &amp; Upgrades
---

### Post by tobias-vogel on 2014-10-12
Hi everybody,

I have a Samsung Ultrabook, approx. 2 years old on which I installed ubunt a while ago.
The Ultrabook comes with one of these Non-UEFI-Secure-Boot-but-still-EFI EFIs capable of emulating a Legacy PC Bios.
Originally I installed Ubuntu using the Legacy Bios method and Grub-Bios bootloader.
Some weeks ago I decided for any reason I cannot recall now, I would like to switch off the Legacy Bios and Boot using the EFI firmware.
Conversion from MBR to GPT went ok, and Grub installed smoothly. However, I am encountering a strange issue I have no explanation for.
When I power up the Ultrabook, I am immediately presented with the "grub cannot find partition ..:", "grub rescue>" shell.
The UUID it prints out does not match any of the partitions of that system.
The workaround to this is to press the shortcut to fire up the EFI/Bios emulation menu, then exiting the menu again immediately, and voila:
it boots!
However I'd preferr rather not to use this ridiculous "Hack" to start my system.

Any ideas, how to fix this?

Thanks!

---

### Post by oldfred on 2014-10-12
What model Samsung?

It sounds like you may be booting an old copy of grub first and then on reboot it boots correct copy of grub. 
If you had installed in BIOS mode originally, you would still have a copy of grub in MBR that then would not be valid.

May be best to see details, but I just installed Boot-Repair yesterday and they must have changed something else as extra -ubuntu is not now in ppa entry.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Note error in above:
fred@trusy-ar:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu[COLOR=#ff0000]-ubuntu[/COLOR]-boot-repair-trusty.list
sed: can't read /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-trusty.list: No such file or directory

fred@trusy-ar:~$ sudo sed 's/trusty/saucy/g' -i /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list

---

### Post by tobias-vogel on 2014-10-14
Thanks for your reply!

It's a Samsung NP900 Ultrabook.

I have thought about that, too, so I wiped the boot-sector of the MBR using
```
dd if=/dev/zero of=/dev/sda bs=446 count=1
```
before installing Grub-EFI.

I considered using Boot-Repair before, however I was unsure, whether the utility
wouldn't just restore my MBR. I'll try that today and report how it worked...

---

### Post by tobias-vogel on 2014-10-14
Well, that's the error I got using Boot-Repair... #-o

[ATTACH=CONFIG]257197[/ATTACH]

---

### Post by oldfred on 2014-10-14
That is reinstalling grub to gpt protective MBR. Since with gpt there is no space after the protective MBR, grub has to have a separate unformatted 1 or 2MB partition with the bios_grub flag. It can be anywhere on drive.

Or you use Windows to install in BIOS mode and it converted drive from gpt to MBR(msdos). But Windows does that incorrectly and leaves a backup gpt partition table. Linux tools check for both MBR & gpt and then get confused. If that is the case use fixparts to remove old gpt data.

If wanting to install in UEFI mode which does require gpt partitioning you must boot Boot-Repair or Ubuntu live installing in UEFI mode not in BIOS mode. The two boot modes are not compatible, (may be why you see what looks like a reboot) as once you start in one mode you cannot change to the other mode except by rebooting or directly from UEFI menu. Some systems require you even to turn on/off UEFI or CSM/BIOS mode in UEFI menu. Some will auto switch or find either way to boot. 
My motherboard would not boot Ubuntu in UEFI mode with Windows OS, had to change to Other OS. I think that meant secure boot but not how worded. And then even with UEFI & BIOS would only boot in BIOS mode. Only with UEFI only could I boot Installer in UEFI mode.

So install and repairs in UEFI mode must be made from a repair disk booted in UEFI mode. I think if you tick UEFI in Boot-Repair it can force a grub-efi-amd64 (efi boot) install when booted in BIOS mode to convert from one mode to the other.

---

