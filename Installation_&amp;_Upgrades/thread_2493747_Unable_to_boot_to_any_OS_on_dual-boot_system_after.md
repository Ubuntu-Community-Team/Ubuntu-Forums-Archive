---
title: "Unable to boot to any OS on dual-boot system after failed Ubuntu upgrade"
date: 2023-12-23
forum: Installation &amp; Upgrades
---

### Post by malhonen on 2023-12-23
Hi everybody,

I have had Ubuntu 23.04 lunar and Windows 10 on my refurbished 64-bit HP EliteBook 840 G4 for some months now, and both systems have worked fine. Last Monday, Ubuntu notified me that there is a new dist-upgrade for 23.10 mantic, and I pressed update. The process finished with an error saying:

> An unresolvable problem occurred while calculating the upgrade.

 This was likely caused by:
 * Unofficial software packages not provided by Ubuntu Please use the tool 'ppa-purge' from the ppa-purge package to remove software from a Launchpad PPA and try the upgrade again.

So I googled and found a suggestion that I should run "pro security-status --thirdparty" and "pro security-status --unavailable", which I did and decided to do "sudo apt purge net.downloadhelper.capp" to remove a companion app to a Firefox extension called Video DownloadHelper in case it was the culprit. Well, it wasn't, as the subsequent try on dist-upgrade failed with the same terms. Dist-upgrade said it had restored the system to its initial state but then when I booted the machine and tried to start Windows, grub gave an error about a missing boot file for Windows. The menu item was still there but it would just not boot to Windows whereas Ubuntu still worked normally. I tried doing update-grub but for some reason it didn't detect Windows at all and removed it from the grub menu altogether. /etc/default/grub had GRUB_DISABLE_OS_PROBER set as "false", so that was not the issue. Running os-prober separately, I got zero output, too.

Next, I grabbed a USB drive where I had earlier burned Rescatux 0.74, launched it and pressed on a couple of items I thought might provide a solution. I don't remember the order anymore but I think I selected "Restore Windows MBR", "Restore Grub", "Update Grub Menus" and "Easy GNU/Linux Boot Fix". I'm quite sure I did not press "Fake Microsoft Windows UEFI" or "Reinstall Microsoft Windows UEFI". After this procedure, I rebooted, and Grub wouldn't show up at all. Instead, I would see a message saying "No boot signature in partition" and then after a few seconds "BootDevice Not Found. Please install an operating system on your hard disk. Hard Disk - (3F0)".

My next attempt to fix the situation that had gotten worse was to chroot from the live Rescatux drive and do install-grub and update-grub but they didn't change anything. Next I decided to try YannUbuntu's boot-repair, so I installed it from his PPA on the live Rescatux system and did "Recommended Repair". That didn't make the situation any better, and the funny thing was that in addition to my hard drive /dev/sda, boot-repair insisted on fixing the Rescatux USB drive /dev/sdb, as well. Finally, I decided to download the boot-repair ISO image and burned it on another USB. That seemed to work a little bit better as now boot-repair understood that I was trying to fix /dev/sda and not /dev/sdb. Boot-repair said that it had detected a Legacy Windows on my computer and recommended that I would deactivate the separate /boot/efi partition. After I did that, boot-repair said it had detected GPT and asked me to create a BIOS-Boot partition. I did not want to change anything in my partition table because just a day earlier everything had worked fine with the existing settings, so I went back, activated the separate /boot/efi partition again and pressed "Continue Anyway" when boot-repair warned about LegacyWindows. The process finished with "Boot successfully repaired" but when I rebooted the machine, I got "No boot signature" and "BootDevice Not Found" again.

Since boot-repair had mentioned Legacy Windows, I decided to try different combinations of Legacy/UEFI support in my BIOS and run boot-repair again. My BIOS has three options: 1) "Legacy Support Enable and Secure Boot Disable" (which I think was selected in the beginning of the process), 2) "Legacy Support Disable and Secure Boot Enable", and 3) "Legacy Support Disable and Secure Boot Disable". With each one of these, boot-repair would do something but neither of the operating systems would boot, so in the end I went back to BIOS setting number 1 and ran boot-repair once more, saying "Continue Anwyay" despite Legacy Windows, as I had done during my first try. In the end, boot-repair told me the following:

> Boot successfully repaired.

Locked-NVram detected. (Ubuntu) Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Please do not forget to make your UEFI firmware boot on the Ubuntu 23.04 entry (sda2/efi/ubuntu/grubx64.efi file) !

I have no idea how to proceed. After removing the live USB drive, I see three options in my BIOS boot menu: "UEFI - SanDisk SSD PLUS 1000GB", "Legacy - SanDisk SSD PLUS 1000GB" and "Boot from file". The first two give me "No boot signature" and the third one "No media found". My partition table is as follows:

> Model: ATA SanDisk SSD PLUS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: pmbr_boot

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  556MB   555MB   ntfs         Basic data partition          hidden, diag
 2      556MB   660MB   104MB   fat32        EFI system partition          boot, esp
 3      660MB   676MB   16.8MB               Microsoft reserved partition  msftres
 4      676MB   323GB   322GB   ntfs         Basic data partition          msftdata
 6      323GB   1000GB  677GB   ext4
 5      1000GB  1000GB  681MB   ntfs                                       hidden, diag

where sda1 is practically empty (empty Recovery folder in addition to "System Volume Information"), sda2 is normally mounted as /boot/efi (according to /etc/fstab), sda3 is unmountable, sda4 my main Windows partition, sda5 a recovery Windows partition with a couple of files under Recovery/WindowsRE plus a file called $WINRE_BACKUP_PARTITION.MARKER, and sda6 my main Ubuntu partition. sda2 has a folder called EFI with subfolders "boot", "Microsoft" and "Ubuntu". Rescatux had made a backup of the whole EFI folder when I first started fiddling with it, and since things had started going worse after that, I eventually renamed the backup folder to "EFI" but that didn't help, either.

I have attached the outputs of "efibootmgr", "gdisk -l/dev/sda", and "blkid" in case any of that helps in the analysis. The boot-info file of the last boot-repair run is posted at [https://pastebin.ubuntu.com/p/yvqnnvpkSF/](https://pastebin.ubuntu.com/p/yvqnnvpkSF/) . I would greatly appreciate any help or pointers, as currently the system is unusable. I don't have access to Windows installation media, as Windows 10 was preinstalled on the laptop, but I do have a Ubuntu 23.04 installation USB drive that I am now using as a live system to write this message.

---

### Post by oldfred on 2023-12-23
Before attempting any repairs with systems that can boot in either UEFI or BIOS mode, you must know if your installs are UEFI or BIOS.
Hardware since 2012 is UEFI, when Microsoft requried vendors to install in UEFI boot mode to gpt partitioned drives.
And Windows only boots in UEFI mode from gpt drives, so Windows must be an UEFI install, no matter what Boot-Repair says.
I thought Yann was fixing that error in Boot-Repair.
And recommending bios_grub is only for BIOS boot of Ubuntu. But you really want all installs in UEFI boot mode.

So only boot in UEFI mode. You usually have to choose each time you boot USB flash live installer or Windows repair/recovery flash drive.
UEFI/BIOS mode setting in UEFI settings, is for installed systems. Usually does not apply to USB boot. You want UEFI only.

You now show no UEFI boot entry in UEFI, starting at line 194.
If running efibootmgr to see boot entries always run this which gives details on GUID/partUUID used for ESP partition.
sudo efibootmgr -v

Does sda2 have esp,boot flags? Boot-Repair seems to think it does not and that may be issue on reinstalling boot loaders in UEFI boot mode.
Use gparted from live installer and right click on partition to set flags.

---

### Post by tea for one on 2023-12-23
```
Model: ATA SanDisk SSD PLUS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: [COLOR="#FF0000"]pmbr_boot[/COLOR]
```
Did one of your rescue attempts add an unusual flag [COLOR="#FF0000"]pmbr_boot[/COLOR] to the disk?
Apparently, according to my research, it should not be present for UEFI boot mode.
In a "Try Ubuntu" session, open a terminal:-
```
sudo parted /dev/sda [COLOR="#0000FF"]# check your disk identity is correct[/COLOR]
(parted) disk_set pmbr_boot off
(parted) quit
```

---

### Post by malhonen on 2023-12-23
> **tea for one said:**
> Did one of your rescue attempts add an unusual flag [COLOR=#FF0000]pmbr_boot[/COLOR] to the disk?
Apparently, according to my research, it should not be present for UEFI boot mode.
In a "Try Ubuntu" session, open a terminal:-
```
sudo parted /dev/sda [COLOR=#0000FF]# check your disk identity is correct[/COLOR]
(parted) disk_set pmbr_boot off
(parted) quit
```

Thanks a lot! This fixed the problem with grub, so now I can boot into Ubuntu as usual. Windows doesn't show up in the grub menu, though, and update-grub and os-prober don't find it. Should I now try running boot-repair again from Ubuntu or the boot-repair USB drive?

> Does sda2 have esp,boot flags? Boot-Repair seems to think it does not  and that may be issue on reinstalling boot loaders in UEFI boot mode.

Yes, sda2 has those two flags and already had them before applying the pmbr_boot fix.

---

### Post by malhonen on 2023-12-23
I identified the problem with booting Windows. For some reason, the folder EFI/Microsoft/Boot did not have files named "bootmgr.efi" or "bootmgfw.efi" at all, so I copied them from the folder Rescatux had created while attempting to fix the problem earlier, and ran update-grub again. Now Windows was detected, and I was able to boot to it. Wonder how the files got deleted in the first place, whether the failed mantic upgrade did it or if something else had happened in Windows before that. In any case, now everything works. Thank you all for your invaluable help!

---

### Post by tea for one on 2023-12-23
If you look at lines 135 - 142 of the report, you are missing the Windows boot files:-
```
/efi/Microsoft/Boot/bootmgfw.efi 
/efi/Microsoft/Boot/bootmgr.efi
```

Can you double-check that the Microsoft folder is located in the EFI directory?

Edit: I hadn't seen post no. 5

Don't forget to mark the thread as solved - it's helpful to other forum users.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by malhonen on 2023-12-23
One last update: I was able to boot to Windows using grub but then Windows replaced grub with its own bootloader, so when I rebooted, Windows came up automatically. To fix the situation, I opened Command Prompt with administrator rights and typed: "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi". That restored grub and now I can freely switch between the two systems.

---

### Post by tea for one on 2023-12-24
> **malhonen said:**
> One last update: I was able to boot to Windows using grub but then Windows replaced grub with its own bootloader, so when I rebooted, Windows came up automatically. To fix the situation, I opened Command Prompt with administrator rights and typed: "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi". That restored grub and now I can freely switch between the two systems.
Alternatively, you can set Ubuntu to be the priority boot OS.

Power on and press F10 to access HP UEFI set up
System Configuration > Boot Options > OS Boot manager (under UEFI Boot Order)

If Ubuntu is the first option, then the PC will boot Ubuntu first.
You can change the default with F5 and F6 keys.

---

