---
title: "GRUB problems"
date: 2017-07-15
forum: Installation &amp; Upgrades
---

### Post by morbuscordis on 2017-07-15
So, I recently decided to attempt an installation of Ubuntu onto a USB drive. Despite being sure I was installing the bootloader onto the USB drive and not the internal HDD, apparently this was not the case. The problem I have now, is that my PC boots into Windows Bootloader automatically, however Ubuntu Bootloader is displayed as a boot option.
What's the best way to remove the GRUB bootloader without damaging the Windows Bootloader or Windows?
I am using Windows 10 Home Edition, and I have tried the automatic repair option in firmware. I am just given an error message. Any help would be appreciated, thanks.

---

### Post by oldfred on 2017-07-15
USB drives in UEFI mode only boot from ESP on USB drive and /EFI/Boot/bootx64.efi. Grub does not create that folder & file with standard install.
You can copy /EFI/ubunbu twice from ESP on sda to ESP on sdb, but second copy needs to be in /EFI/Boot and then rename shimx64.efi to bootx64.efi.

Once you confirm that from UEFI you can boot external, then you can delete /EFI/ubuntu folder on internal drive and use efibootmgr to remove entry in UEFI boot menu.
But you should be able to use UEFI boot menu and choose the entry in UEFI to boot USB drive as long as it is plugged in. But I would still do the copy to USB drive, just as another way to boot if needed.

What Brand/model system?

See this and link in my signature below:
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

---

### Post by morbuscordis on 2017-07-15
My laptop is an HP OMEN 15-ax203na. I don't know what I did wrong, but I may have selected the wrong drive to install the boot manager to. The drive was listed as sdc1, but I assumed that sdb was the drive on which I had the installation media.
I'm fairly new to Linux, especially the whole directory system, so I apologise if I've been a complete idiot.

---

### Post by morbuscordis on 2017-07-15
Specifically, what steps must I take to remove the GRUB bootloader from my single boot Windows 10 PC. I have both the Windows Bootloader and GRUB, which is problematic, especially if I do not have the USB drive inserted. My laptop has no disk tray So I had to use Usb installation media.

---

### Post by morbuscordis on 2017-07-15
And the USB stick in question, is a SanDisk extreme GO 3.1 64gb

---

### Post by yancek on 2017-07-15
Removing UEFI boot entries from windows is explained at the MICROSOFT site at the link below:

[https://answers.microsoft.com/en-us/windows/forum/windows_8-desktop/edit-uefi-partition-how-to-remove-ubuntu-folder/1718f140-7b06-4046-b449-3065b260be30](https://answers.microsoft.com/en-us/windows/forum/windows_8-desktop/edit-uefi-partition-how-to-remove-ubuntu-folder/1718f140-7b06-4046-b449-3065b260be30)

---

### Post by oldfred on 2017-07-15
If you remove grub you will not be able to boot install on USB drive. You also should be able to boot Windows using UEFI boot menu at any time.

To remove grub, you need to remove the /EFI/ubuntu folder in the ESP and remove the ubuntu entry in the UEFI boot menu.
 UEFI How To Remove Ubuntu From A Computer Dual Booting With Windows 10 (UEFI only)
How To Remove Ubuntu From A Computer Dual Booting With Windows 10
[http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html](http://www.everydaylinuxuser.com/2016/04/how-to-remove-ubuntu-from-computer-dual.html)
Delete /EFI/ubuntu folder from Windows
[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi) 

      
 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079
[/URL]
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079) 

[URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]
[/URL]

---

### Post by morbuscordis on 2017-07-16
Thanks all, problem is now solved (I believe). :)

---

### Post by morbuscordis on 2017-07-16
And Oldfred, it's escape + F9 for boot menu, F10 for bios setup. Would I have to enable Legacy Support to boot into Ubuntu, supposing that the bootloader was installed on the USB stick?

---

### Post by morbuscordis on 2017-07-16
I have two USB ports on the left (2.0 and  3.1), and 1 on the right (3.1) The USB stick was plugged into the right (I'd prefer to use 3.1, and I can't plug it in next to the SanDisk Cruzer blade (install media) because it's too fat. What do you suggest?

---

### Post by oldfred on 2017-07-16
And have you updated UEFI from HP? Note that will reset most UEFI settings. I document all my settings so I can easily redo them. With BIOS everything was reset, now with UEFI some settings are saved. 

Have seen some posts about HP only working with certain USB ports for booting, but I think it was older models.        Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260) 
    
Often better to use UEFI mode. But most UEFI will let you use Legacy mode, you may have to choose or change settings in UEFI to enable it. And Legacy/BIOS/CSM only works with UEFI Secure Boot off.
I configure all new drives and larger flash drives with gpt and both the ESP & a bios_grub. But with my newer UEFI systems in UEFI mode do not need the bios_grub, but it is only 1MB, so I still like to have it in case I want to configure system for BIOS boot.

You can install to one flash drive in any port and if HP lets you boot from other ports, then can plug it into any other port. With Ubuntu you usually can install from another totally different system as long as you do not install proprietary drivers. Sometimes boot parameters needed to boot as system needs proprietary drivers, but it will boot.

If you have to use USB2 port it will be slow. My old BIOS system only had USB2 ports and writes were very slow. I did find that USB3 flash was about 10% faster on my USB2 ports, so started only buying USB3 drives even though I then had not system with USB3 ports.

---

