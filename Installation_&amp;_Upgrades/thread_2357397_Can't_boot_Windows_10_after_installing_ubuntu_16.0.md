---
title: "Can't boot Windows 10 after installing ubuntu 16.04 LTE"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by ryan1872rfc on 2017-04-01
Hi all,

I am new to Linux and Ubuntu and I have recently installed Ubuntu on a new partition alongside Windows 10 and now I cannot boot windows, all though Ubuntu boots perfectly fine. I have tried multiple fixes including boot-repair none of which a succeed . I have also modified 'grub.cfg' to include an option for Windows in the GRUB 2 boot menu but when I select it goes to a black screen then back to the grub boot menu.

I have included a paste bin link to my boot info summary below.
[URL="http://paste2.org/Ee3t0WNV"]http://paste2.org/Ee3t0WNV
[/URL] 
Any help will be greatly appreciated as I have spent two day trying to solve this:confused: and I do not want to lose my data from windows partition.

---

### Post by yancek on 2017-04-01
Your boot repair output shows that you have both an EFI partition and a BIOS boot partition.  Your system uses GPT partitioning so windows requires that you use EFI.  If you need EFI for one OS, then other OS's on the same drive need to be EFI also or you are going to have boot problems. You do have EFI files for both Ubuntu and windows so you should have a setting in your BIOS to use UEFI and should also have the option to use a specific key (F12??) on boot to make a selection

---

### Post by ryan1872rfc on 2017-04-02
Yes I do have an option in bios setup to use "legacy boot mode" which I have enabled but no to avial, on my boot mode select screen I have 2 options that are the same for ubuntu, I also have an option for "notebook hard drive" which when selected goes to a grub rescue screen. And there is an option for boot from EFI file which takes me through menus to select which file but none of them work only giving me the message "selected boot device failed"...

And also, When I select OS boot manager it comes up with the message "error: file '/boot/grub/i836-pc/normal.mod' not found."

Completely stumped on this one

---

### Post by yancek on 2017-04-02
> EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option.

I see the above message at the bottom of your boot repair output.  None of your partitions are marked as active/bootable so that might do it.  The EFI boot partition is sda2.  I don't know if there is an option to do that in boot repair but you can use GParted to do it and GParted is on the Ubuntu installation disk.

---

### Post by oldfred on 2017-04-02
The sda2 says EFI System partition, so it must have boot flag.
The use of boot flag by parted/gparted is just to set the very long GUID that makes a FAT32 partition the ESP - efi system partition.

You have grub installed in gpt's protective MBR for BIOS boot, but fstab shows mounting of efi partition, so you now have both Windows & Ubuntu configured for UEFI boot. Windows will only boot in UEFI mode from gpt partitioned drive, so do not turn on Legacy/CSM/BIOS boot mode.

Grub will only boot working Windows. And that means it cannot need chkdsk nor is hibernated. And Windows fast start up is always on hibernation. Did you turn that off? You still should be able to directly boot Windows from UEFI one time boot menu. And if issues with Windows you may be able to press f8 to get into repair console. Otherwise you need your Windows repair/recovery disk that you should have made as soon as you got system with Windows.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html
[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 

[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

### Post by ryan1872rfc on 2017-04-02
Thanks guys,

I have tried marking EFI partition as bootable with gParted with no success, also tried turning off legacy boot mode and no luck. Unfortunately I don't have a repair disk for windows and no way of creating one. I'm thinking my only option to fix this would be to back up the windows partition to another partition, and then delete all other partitions apart from linux and reinstall windows ?

I've included some caps of what BIOS screens I am getting, and also my current partitions.
[U]
**PARTITIONS**[/U]
[https://drive.google.com/file/d/0By638Q4LyzpKM0lUVDFxd3EtMmM/view?usp=sharing](https://drive.google.com/file/d/0By638Q4LyzpKM0lUVDFxd3EtMmM/view?usp=sharing)

_**BOIS SCREENS**_
[https://drive.google.com/file/d/0By638Q4LyzpKTS1qTnlKNWlONzIyZXBrcVVqOFFVanczc3RF/view?usp=sharing](https://drive.google.com/file/d/0By638Q4LyzpKTS1qTnlKNWlONzIyZXBrcVVqOFFVanczc3RF/view?usp=sharing)
[https://drive.google.com/file/d/0By638Q4LyzpKUkg0d1NJRWdWcUF6VVd6dnNnSmhhODJlVGdj/view?usp=sharing](https://drive.google.com/file/d/0By638Q4LyzpKUkg0d1NJRWdWcUF6VVd6dnNnSmhhODJlVGdj/view?usp=sharing)
[https://drive.google.com/file/d/0By638Q4LyzpKdlE2TlNRSmxkVG16TkRkX1o1SXpzaDE5OEdB/view?usp=sharing](https://drive.google.com/file/d/0By638Q4LyzpKdlE2TlNRSmxkVG16TkRkX1o1SXpzaDE5OEdB/view?usp=sharing)

---

### Post by oldfred on 2017-04-02
I did not know gparted had a legacy boot flag. I would suggest removing that, but you also have the esp flag which should be for UEFI boot.

The normal not found is typical of tying to boot in wrong mode. Or it finds grub in MBR and tries to boot that, but you are configured for UEFI boot and must only boot with UEFI.

You may not be showing Windows in boot options if you turned on Legacy/BIOS/CSM boot mode as Windows cannot boot in that mode. You must be in UEFI boot more or UEFI with Secure Boot mode.

What brand/model system?
Some do not make it easy to boot Ubuntu and we have to do work arounds.

If booting Ubuntu live installer and adding Boot-Repair, be sure to boot in UEFI boot mode only, not BIOS.
UEFI should give you two boot options for Ubuntu USB flash drive. One UEFI and one BIOS(probably does not say BIOS anywhere).
This shows first boot screens, so you can immediately tell which way you have booted.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ryan1872rfc on 2017-04-02
It is a HP Pavillion 15 Laptop with Windows 8(amd64) pre-installed.

---

### Post by oldfred on 2017-04-02
HP violates UEFI spec.
They use description as part of boot and for some strange reason only valid description is "Windows Boot Manager".
But UEFI also has a fallback or hard drive entry that still works with HP.
Boot-Repair will now auto copy shimx64.efi to be the fall back /EFI/Boot/bootx64.efi. But you may not have an UEFI entry for the hard drive. You do not yet show that you ran Boot-Repair in UEFI mode, so it would do that copy. Many threads on manually copying files.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

Once you have /EFI/Boot folder and shimx64.efi in that folder renamed to bootx64.efi
Without having to rerun full Boot-Repair report  you can see UEFI entries.

 sudo efibootmgr -v  

 sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition  
Your ESP is sda2 or:

 sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sda -p 2

Check entry is there :
sudo efibootmgr -v




[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

