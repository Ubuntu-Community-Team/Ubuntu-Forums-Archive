---
title: "Can't boot into Ubuntu after shrunk /home partition"
date: 2017-10-27
forum: Installation &amp; Upgrades
---

### Post by cybermyth on 2017-10-27
I have dual boot on my laptop with Windows 10 and Ubuntu installed.

I've shrunk the Ubuntu /home partition using Gparted (with live USB). The /home partition was the last partition on the disk (/dev/sda8) and then I've created a new partition from the available space in Windows 10 (now /dev/sda9).

I can successfully boot into Windows 10, but I could only boot into Ubuntu once. Now I am getting a mount /boot/efi problem. But the strange thing is, if I boot into recovery and do anything in there (like delete broken packages), I can boot into Ubuntu normaly from there, but without graphics drivers enabled (if I understand correctly).

More details with added logs [here]("https://askubuntu.com/questions/968195/cant-mount-boot-efi-after-shrinking-partition-on-dual-boot")

I've ran boot-repair, but it failed. Link to pastebin [here]("http://paste.ubuntu.com/25832274/")

---

### Post by efflandt on 2017-10-27
It looks like you need to disable Windows "fast boot" which is a form of hibernation that marks its partitions as dirty, so nothing else mounts them and it can resume instead of cold boot.

---

### Post by cybermyth on 2017-10-27
I've disabled fast boot now, but no luck. I've also ran the boot-repair successfuly now, but it didn't help.

Logs [here]("http://paste.ubuntu.com/25832657/")

---

### Post by oldfred on 2017-10-27
What brand/model system?

You have two Windows entries in UEFI. One is to boot Ubuntu using shim.
>  Boot0001* Windows Boot Manager	HD(2,GPT,51f3571e-2f45-4341-956d-dce2730a1cb3,0xe1800,0x32000)/File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])WINDOWS 



Years ago with early issues with UEFI & systems that only wanted to boot Windows by description renaming the Windows entry to actually use shimx64.efi was common. But Windows would overwrite it, and when Windows turns back on the fast start up or needs chkdsk, then you could not boot from grub and did not have an UEFI entry.  So that type of entry is not used anymore.

Most systems with the broken UEFI like HP & Sony will still boot the fallback or hard drive entry at /EFI/Boot/bootx64.efi. So Boot-Repair copies shimx64.efi to the the bootx64.efi. Then you can boot a hard drive entry if you have one. We can add on, but unless description is something UEFI accepts it may not work.

The other option is at end of the Summary Report on editing Windows BCD.

---

### Post by cybermyth on 2017-10-27
MSI

Thanks for the info.. If I understand correctly I need to use [COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi to change the default boot entry? I already tried that, but no luck.[/COLOR]

---

### Post by oldfred on 2017-10-27
You did not say model.
But often issues are more common by brand as they use same UEFI with just slight changes for each model.

 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

