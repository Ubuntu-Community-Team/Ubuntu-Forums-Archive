---
title: "&quot;No signal&quot; monitor  for 2 minutes before Grub appears, very slow boot"
date: 2016-01-21
forum: Installation &amp; Upgrades
---

### Post by Nuitblanche on 2016-01-21
I purchased (yesterday) a Lenovo HD Destop Computer, Windows 8.1 64-bit. AMD-7600 3.1 GHz Radeon R7; 7-in-1 Media Card Reader; Gallium 0.4 on AMD KAVERI (DRM 2.43.0, LLVM 3.6.2)  Graphics; 802.11ac Wireless.

First, I backed up the system image to an external disk. Then I installed Ubuntu 15.04 alongside Windows (I disabled "secure mode" in bios and disabled Fast startup in power settings). Ubuntu appeared to have successfully installed. But when I start the PC, it boots directly to Windows 8. No grub. I booted again and pressed F12 to get into bios and there it was - Ubuntu was in the boot sequence. But when I choose the Ubuntu in the boot sequence, it would take so long for Ubuntu to load (during that time the monitor screen is black "no signal" displayed).

Anyways, not liking Windows 8, I decided to just delete it and install Ubuntu (15.10) completely over it, hoping  that Ubuntu will load better if it doesn't have to deal with any dual boot glitches. The installation appeared to have gone well. Alas, the problem remains. At boot up, the "no signal" black monitor comes on and stays for a good 2 minutes before the grub appears. I go to log on screen and everything works alright.

I am guessing that the problem has something to do with the Ubuntu driver not being compatible with Gallium 0.4 on AMD KAVERI  graphics?

Another less important problem:  Ubuntu is not acknowledging the  802.11ac Wireless.
Anyone know how to fix this?  I'd hate to have to reinstall the Windows 8 and return it to the store. 

THANKS.

---

### Post by grahammechanical on 2016-01-21
A couple of points.

1) Windows 8.1 when comes pre-installed on a computer will have been installed in efi mode. That means that Ubuntu needs to be installed in efi mode. If we run the live session in BIOS/Legacy/Compatibility mode then Ubuntu will be installed in BIOS mode and we get the situation that you experienced at first before you re-installed Ubuntu.

2) Gallium 0.4 is the Ubuntu driver. Actually, it is more accurate to say it is the Open Source video driver that is the default in Ubuntu when we do not activate a proprietary video driver.

3) With a UEFI boot system the hard disk will have GPT partitioning. This means that there will be an efi partition where Windows 8 kept its efi boot files. Had Ubuntu been installed in efi mode then the Ubuntu installer would have put some Linux efi boot files in the same efi partition and there is nothing wrong with that.

4) A Linux OS installed on a GPT partitioned hard disk in BIOS mode needs to have a bios boot partition. If Ubuntu was installed in BIOS mode on a GPT partitioned disk then the installer would have created the needed bios boot partition. Maybe not.

It is my guess that the delay in seeing a Grub boot menu is due to confusion coming from having an efi boot partition with efi boot files in it and also a bios boot partition with Ubuntu boot files. Possibly grub itself. The motherboard is checking and double checking where it can find a boot loader.

This just my uneducated guess.

Regards.

---

### Post by Nuitblanche on 2016-01-21
Thanks Grahammechanical. Your uneducated guess is a thousand times more educated than mine.

So how do I fix the efi files-bios boot files so that the mother board doesn't get confused?

or, the other way,  how do I install ubuntu in EFI mode?

---

### Post by Nuitblanche on 2016-01-21
I checked the partitions, there is an efi boot partition as you say: 

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           931.5G            
&#9500;&#9472;sda1 vfat     512M /boot/efi  
&#9500;&#9472;sda2 ext4   924.1G /          
&#9492;&#9472;sda3 swap     6.9G [SWAP]     
sr0            1024M  


Is it possible to add a bios boot partition and instruct the motherboard to boot from there instead and just ignore the efi boot partition? (bummer, when I selected erase Windows and install Ubuntu over it, I thought that it would automatically do everything it needs to do to install properly...)


edit: after the long wait, sometimes it boots into the grub menu, other times it boots direct to the log in screen....

edit (2nd) : 
when I type in command:  [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

I get, 
EFI boot on HDD

---

### Post by Nuitblanche on 2016-01-23
Well am back just to close the thread.

I've already returned the Lenovo to the store because even after I restored the original factories settings and accepted the free upgrade to Windows 10, it became obvious that more problems were just hatching one after the other. If I did not like Windows 8...I hate Windows 10!

Gawd, I'm gonna contribute $20 bucks to Ubuntu now, just to thank them for a SANE operating system and hope they continue their policy and service well into the future!

---

