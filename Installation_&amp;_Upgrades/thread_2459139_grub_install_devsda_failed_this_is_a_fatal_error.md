---
title: "grub install /dev/sda failed this is a fatal error"
date: 2021-03-11
forum: Installation &amp; Upgrades
---

### Post by thestuckboy on 2021-03-11
I'm writing this from Ubuntu Live USB because since this morning i try to install ubuntu as a second OS using GRUB as boot loader. When installing Ubuntu it says "Executing GRUB2 install in dev/sda" and then the error appears again.

Now i can't boot my first OS Windows 10 and i don't know what to erase all the things to get W10 again.

I tried with:


[LIST]
[*]Create a EFI partition with more than 1GB of space 
[*]Create a ext4 partition with more than 30GB of space 
[*]Disable Secure Boot 
[*]Booting in Legacy Mode 
[*]Changing the boot loader installation in the EFI partition. 
[/LIST]

Please i need help i don't want to lose all my files in Windows 10.

---

### Post by Impavidus on 2021-03-11
There are two modes in which you can install operating systems: UEFI and legacy. Better not confuse those. Was this a pre-installed Windows 10 system, or upgraded from a pre-installed Windows 8 system? If so, it must have been installed in UEFI mode, as Microsoft has mandated that since 2012. If you change to legacy mode, Windows will no longer boot. Set it to UEFI mode, which is best anyway (except in some special circumstances). If that doesn't restore Windows booting, the Windows bootloader was damaged and you need a Windows repair disk to fix that.

---

### Post by oldfred on 2021-03-11
What brand/model system?
Can you not boot Windows from UEFI boot menu? As Impavidus suggests make sure UEFI boot is default in UEFI/BIOS settings if Windows is UEFI.
Did you leave Windows fast start up on? That prevents Linux driver from opening Windows type partitions in read/write mode.

Boot-Repair cannot fix most Windows issues, but has a good report to show details of installs and then we can see what issue may be.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by thestuckboy on 2021-03-11
Just recently uninstalled Ubuntu iso from my USB to install Windows 10 and try to use the Repair Tool of Windows, and now I have a second problem. I can’t boot my USB. It just appears "Minimal BASH like line editing is supported"

I checked that USB boot is first in Boot Order And now I'm downloading the Boot Repair Disk Tool from help.ubuntu

Update: Grub works now, I can open Ubuntu, but it doesn't detect Windows 10 so I can't load windows 10. What can i do now?

---

### Post by tea for one on 2021-03-11
While you are in Ubuntu, please open a terminal and run:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```
This will tell us how you installed Ubuntu

---

### Post by thestuckboy on 2021-03-11
This is the return:

[https://prnt.sc/10j3n1c](https://prnt.sc/10j3n1c)

---

### Post by oldfred on 2021-03-11
For terminal output please just copy & paste.
If more than a couple of lines use code tags.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then ```
 at the beginning and 
``` at the end. 
( [noparse]```
 and 
```[/noparse] )

Windows does not make it easy to create a Windows bootable flash drive from the ISO except from Windows.
Not sure if they have since updated it, but .win file was over 4GB and would not fit on a FAT32 flash drive which is required for UEFI boot.
If you create Windows installer from Windows, then it splits .wim file into two parts so it fits. It used to be with older versions of Windows the .wim was smaller & you could just extract ISO to flash drive to have it boot in UEFI mode.

If you created flash drive with dd, you have to use dd to erase the partition table area to make it usable again.
Reset USB flash that was dd'd to make it usable again, reuse
[https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266](https://askubuntu.com/questions/939230/formatting-a-usb-stick-unable-to-operate-usb/939266#939266) & 
[https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive](https://help.ubuntu.com/community/mkusb#Re-use_the_pendrive) & 
[https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection](https://unix.stackexchange.com/questions/216152/usb-disk-read-only-cannot-format-turn-off-write-protection)

---

### Post by tea for one on 2021-03-11
Your screenshot states that you have installed in UEFI mode, which should be the same mode as Windows 10.

Therefore, you should be able to boot Windows 10 via UEFI (as suggested by [COLOR="#0000FF"]oldfred[/COLOR] in post 3)

Do you know how to do this?

---

