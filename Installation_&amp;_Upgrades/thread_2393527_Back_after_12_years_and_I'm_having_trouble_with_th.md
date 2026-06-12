---
title: "Back after 12 years and I'm having trouble with the first boot."
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by adastra23 on 2018-06-04
I just installed Ubuntu on a Dell 14 3000 and I can't figure out how to get it to boot into Ubuntu after the install. I get a Dell diagnosis instead.
Tried this... Boot-repair
Any help you guys can see there is greatly appreciated.
[http://paste.ubuntu.com/p/dvmhQ8vGjH/](http://paste.ubuntu.com/p/dvmhQ8vGjH/)

---

### Post by oldfred on 2018-06-04
You have an UEFI Windows entry, and it looks like you booted the Ubuntu installer in UEFI mode for Boot-Repair.
But Boot-Repair says it is installing to MBR, not to ESP - efi system partition?
And says no ESP was found.

Script does not fully parse mmcblk devices, so bit more difficult to know what is where.
Post this:
sudo parted -l

Is drive gpt?
Do you want UEFI or BIOS boot?

---

### Post by adastra23 on 2018-06-04
Thanks for your help. I had GRUB before but this were floppy days. Booted Badger and XP.   I don't know MBR or ESP 

Sudo parted -| didn't do much. Just got a >
I was just under the impression that it was UEFI on this machine. I really don't know what's going on here. I changed from fastboot and now I get missing operating system. 
I'm not getting a grub screen, I'm getting the dell f2 f12 screen

---

### Post by adastra23 on 2018-06-04
Do I reinstall with another partition scheme? I don't understand the part about making a fat partition.

---

### Post by ubfan1 on 2018-06-04
UEFI booting requires a small (100M-300M) FAT partition for the bootloaders.  Probably 100M would do it since there's no Windows bootloaders left on the system.    The rest of the 32G may be root, since swap these days  uses a file instead of a partition.  Since the boot-repair USB booted in UEFI mode, the installer should too.  With 2G of memory, try xubuntu or lubuntu, instead of ubuntu.

---

### Post by Dennis N on 2018-06-04
> Sudo parted -| didn't do much. Just got a >

That command should be:
```
sudo parted -l 
```
with lower-case letter l after the dash. Please try again. This will inform others about the current partition setup.

---

### Post by adastra23 on 2018-06-05
Got it working!!
UEFI stumped the guy I asked at work.
I reinstalled making that FAT partition. Used the yannubuntu boot-repair and point the UEFI to the correct file. 
Thanks all.
All three of you helped.
Mark as solved please.

---

