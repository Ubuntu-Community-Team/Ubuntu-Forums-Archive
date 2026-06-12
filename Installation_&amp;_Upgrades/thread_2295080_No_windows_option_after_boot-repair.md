---
title: "No windows option after boot-repair"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by brentdur on 2015-09-15
I am trying to set up a dual boot, windows 8 and ubuntu-gnome. I installed windows 8, leaving a sizable partition for ubuntu, then installed ubuntu in several different partitions. I then ran boot-repair so I could dual boot but windows 8 is not an option in the grub menu, the ubuntu option is present and works correctly.

Here is the pastebin from boot-repair
[http://paste.ubuntu.com/12423914/](http://paste.ubuntu.com/12423914/)

---

### Post by grahammechanical on 2015-09-15
At the bottom of the boot repair report you will read why Grub is not detecting Windows 8. It is because Windows 8 does not shutdown but hibernates instead. Note the comment: No hibernation or fast restarting.

Regards.

---

### Post by brentdur on 2015-09-15
So how do I boot into windows to make sure it does a shutdown instead of a hibernate?

I reset the Windows drive using ntfsfix. And I ran the boot-repair utility again, however Windows is still not an option on the grub menu?

Here is the new pastebin, can you see what is wrong? [http://paste.ubuntu.com/12424574/](http://paste.ubuntu.com/12424574/)

---

### Post by Bucky Ball on 2015-09-16
Have you changed your BIOS to reflect this instruction?

> Please do not forget to make your BIOS boot on sda (1000GB) disk!

---

### Post by brentdur on 2015-09-16
Yes. The grub menu boots, the ubuntu option works, but there is no windows option.

---

### Post by oldfred on 2015-09-16
If with a BIOS/MBR install, you have to have Windows fast start up off.
But with BIOS, you probably have to temporarily reinstall the Windows boot loader to the MBR so you can even boot into Windows to turn it off.
You can use Boot-Repair to install a Windows type boot loader, but much better to use your Windows repair flash drive. Grub only boots working Windows, Boot-Repair can only do minor fixes to Windows and Windows breaks. So you need another way to boot and repair Windows.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
Fast startup is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked 
powercfg /h off

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by brentdur on 2015-09-16
Repaired the windows boot, went into windows double checked to make sure fast startup was off, made sure hiberate was also unchecked, ran powercfg /h off, went back to ubuntu live CD, run boot-repair, still no windows in the grub menu.

Newest pastebin is: [http://paste.ubuntu.com/12429897/](http://paste.ubuntu.com/12429897/)

---

### Post by oldfred on 2015-09-16
You have UEFI hardware, but your installs are in BIOS/MBR mode.

You ran Boot-Repair in UEFI mode.
 > BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

UEFI and BIOS are not compatible, once you start booting in one mode you cannot switch. You can only choose how you boot from UEFI menu and may have to turn on/off UEFI or CSM settings.

So grub tried to update using UEFI, but then only looks for UEFI installs.

If in your Ubuntu run this.
sudo update-grub

And try to only boot Boot-Repair in BIOS/CSM/Legacy mode.

---

### Post by brentdur on 2015-09-16
Should I bother converting my installations to UEFI or is it fine to leave them as BIOS. Neither has any information on it so now would be the time to do it.

If I should convert them (uninstall and reinstall them) how should I go about making sure they install in UEFI instead of BIOS?

And now my Windows installation appears and correctly boots, thank you!

---

### Post by oldfred on 2015-09-16
I would not change since installed.
Windows is a bigger hassle to convert. But Windows will want to update to 10 and that can cause issues with partitions as well as grub in MBR. Back up partition table and keep Ubuntu live installer handy.

If you upgrade Window do this first, but you cannot change any partitions manually if you want to use it, to restore a Linux partition that Windows updates seem to delete.
 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

I would not think it is worth changing, but these are the advantages of UEFI with gpt partitioning.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by brentdur on 2015-09-16
Awesome! Thanks for all your help

---

