---
title: "regular boot goes to grub rescue after boot repair"
date: 2017-12-12
forum: Installation &amp; Upgrades
---

### Post by g8p on 2017-12-12
Paste link: [http://paste.ubuntu.com/26172477/](http://paste.ubuntu.com/26172477/)


My current drives:

##########################################
*****Internal*****
*SSD with Windows 10 installed
*HDD with some Windows files
*HDD that I used for the Ubuntu install attempt

*****External*****
*HDD with a partition holding Windows recovery and
    a second partition with a backup of personal files
*Thumb drive with a bootable version of Ubuntu
##########################################

Hardware:

##########################################
CPU: Intel i7 4770k
Motherboard: Asus maximus hero vi
##########################################


I can still access the BIOS and therefore boot to Ubuntu from the
thumb drive and to Windows Recovery which allows me to use an
Administrator command prompt but not much else.

As stated in the subject line, the default boot option takes me to grub
rescue. It starts with the message:
"error: file '/boot/grub/i386-pc/normal.mod' not found."

I tried to get grub rescue to boot on sde1/EFI/ubuntu/shimx64.efi
like boot repair mentioned but I can't seem to find it.


Thank you so much for your time!

---

### Post by oldfred on 2017-12-12
You have UEFI hardware.
And you have Windows booting in BIOS mode which requires a MBR(msdos) partitioned drive which you have.
And you have Ubuntu installed to another MBR disk for BIOS boot. But your fstab shows a mount of the efi system partition (ESP), which means you installed Ubuntu in UEFI mode. But Ubuntu only installs correctly in UEFI mode to a second drive if you have an ESP on drive seen as sda.

You should be able in BIOS boot mode, totally reinstall grub(grub-pc) in BIOS boot mode which should uninstall grub-efi-amd64(UEFI boot).
You show live installer booted in UEFI mode, reboot in BIOS mode and in Boot-Repair's advanced options choose total uninstall/reinstall of grub and select sdc as location of grub boot loader. And set BIOS to boot sdc, grub should update to include boot of Windows if not hibernated or Windows 10 fast start up is on, which is hibernation. But grub can only offer to boot other installs in same boot mode as UEFI & BIOS are incompatible, or once you start from UEFI in one boot mode you cannot change. A few do have mixed modes, but always have to use UEFI boot menu to boot.

Do not use Boot-Repair's autofix as that installs grub to all drives.
And you want a Windows boot loader in sda. Boot-Repair should offer to install a Windows type boot loader (syslinux) or you can use your Windows repair disk and fixMBR command. Windows only installs in UEFI boot mode to gpt partitioned drive.

Normal not found is typically from version of grub differences, or UEFI vs BIOS boot.

Since you have Windows in BIOS boot mode, best to have Ubuntu in BIOS boot mode, but there are advantages to UEFI and gpt. You already have several drives as gpt.

You could reinstall Ubuntu in BIOS boot mode, but on a gpt partitioned drive. And include both an ESP and bios_grub (1MB unformatted with bios_grub flag) so grub will correctly install in BIOS mode to a gpt drive. And the ESP is for future use, but allocates space, so drive does not have to be totally reformatted. And it really does not use much of total drive space.

Did you need nomodeset to install?
You may need it to boot after install, or until you install the nVidia driver from Ubuntu repository. 
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by g8p on 2017-12-12
Extremely informative as well as helpful, I truly appreciate it.
Seeing as my drives are already MBR partitioned I feel I may as well stick with BIOS boot mode for both. Unless of course, there is some significant advantage to using a gpt partitioned drive along with UEFI boot mode which I have yet to find.

I learned a ton and once again, thank you for your time. I'll be sure to follow the instructions closely.

---

### Post by oldfred on 2017-12-12
BIOS boot is ok.

I did start converting my BIOS system's new drives to gpt back in 2010, XP was BIOS/MBR on a separate drive (and soon retired). And all new drives were then partitioned as gpt. Then when Windows converted to UEFI/gpt I knew eventually I would have an UEFI system and started adding both an ESP for future use and the required bios_grub for my old BIOS system.

Most of the advantages are minor:

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

