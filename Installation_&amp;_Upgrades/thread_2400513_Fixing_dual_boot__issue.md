---
title: "Fixing dual boot  issue"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by apayani3 on 2018-09-06
I recently updated my Ubuntu from 16 to 18 on a dual boot machine with windows 10
Now the windows is not showing in the grub menu and when I run the boot-repair it gives me the error

_*"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.*__*Alternatively, you can retry after activating the [Separate /boot/efi partition:] option."*_


Here is the boot-repair report for my machine,
[http://paste.ubuntu.com/p/DwJJWP5Yh7/](http://paste.ubuntu.com/p/DwJJWP5Yh7/)


I think the new Ubuntu installation has changed the type of my boot partition from UEFI . 
How can I fix this,
I appreciate the help.

---

### Post by oldfred on 2018-09-06
The bios_grub partition is only for BIOS boot on gpt partitioned drives.
Which may be what you want. You can use gparted and make a 1 or 2MB unformatted partition and add bios_grub flag (right click).

You have Windows in BIOS boot mode in sda. But need to move boot flag to sda1 using gparted and with Boot-Repair & advance mode install a Windows boot loader to sda, or you can use your Windows repair flash drive to fix Windows.  But probably need boot flag moved for fixes to work. In Windows it is the make active command which tells Windows which partition is bootable. 

UEFI & Windows are not compatible. You can dual boot that way if you want but only from UEFI boot menu will it work. Once you start booting in one mode, you cannot switch, or grub will only offer to boot other systems in same boot mode. If you add bios_grub and use Boot-Repair to install grub-pc version for BIOS boot then you can set BIOS to boot sdb drive and boot both Windows & Ubuntu from grub. But grub only boots working Windows, so if Windows need chkdsk or turns it fast start up or hibernation back on, you may be able to directly boot Windows from BIOS and Windows drive.


If you just updated, it should not have converted from BIOS to UEFI. So did you reinstall something?
It almost looks like you reinstall Windows in BIOS/MBR boot mode?

---

