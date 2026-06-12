---
title: "Dual booting Windows 8.1 and Ubuntu?"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by Robert_Smith on 2014-01-24
I still have that installation disc around from yesterday and seeing how I have 2 1TB hard drives on my main rig, I am thinking about dual booting Ubuntu 13.10 and Windows 8.1 - how would I go about doing that? I'm still pretty much new to Linux, my previous experience with it accidentally broke an old computer :P

---

### Post by oldfred on 2014-01-24
Since it does not sound like a pre-installed Windows with UEFI & secure boot, did you install Windows 8 in UEFI mode or BIOS boot mode. Many newer systems can work either way.

Then are both drives gpt partitioned or both MBR(msdos)?

Windows only boots from gpt partitioned drives with UEFI.
Both Ubuntu and Windows only boot from MBR drives with BIOS.
But Ubuntu will boot from a gpt partitioned drive with either UEFI or BIOS, so when you have a drive that will never install Windows in BIOS boot mode, I suggest the newer gpt partitioning. 

Post this:
sudo parted -l

 [https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by Robert_Smith on 2014-01-24
I built my computer myself, installed Windows 8 from a disc. 
Specs
Processor - Intel i5-3570k
HDD - 2TB HDD
Graphics Card - Radeon HD 7950
OS - Windows 8.1
RAM - 16GB
PSU - Corsair HX 1050
MOBO - ASRock Z77 Extreme4

---

### Post by Robert_Smith on 2014-01-24
So which boot mode is mine? I built it myself... I was wondering if I could get instructions. I know that when I tried to install it on my older Vista computer it gave me the option (in the installer) of Install and wipe Vista off the computer or Install alongside Vista, in the actual installer. Would a Windows 8.1 machine work the same way?

---

### Post by Robert_Smith on 2014-01-24
After some thought I think I have a BIOS not a UEFI because a screen shows up on boot that says ASROCK...

---

### Post by fantab on 2014-01-24
Boot with Ubuntu Live DVD/USB and "Try ubuntu (without installing)". Open Terminal [Ctrl+Alt+T], run the following command and post its output here:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by oldfred on 2014-01-25
Your motherboard has both UEFI & BIOS modes. 
How you boot install media from UEFI menu for both Ubuntu & Windows is how it installs. You should see two entries for a flash drive, one UEFI and one not, but descriptions are not always clear.

Run fantab's suggested commands. 
If drive is gpt partitioned and you have an efi partition formatted FAT32 then it is UEFI. 
If MBR(msdos) and Windows has a 100MB boot and main install only then you have installed in BIOS mode.

---

### Post by Robert_Smith on 2014-01-25
Ok. I'll get to booting Ubuntu and typing those commands

---

