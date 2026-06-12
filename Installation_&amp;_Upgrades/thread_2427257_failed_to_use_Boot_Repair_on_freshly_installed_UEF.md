---
title: "failed to use Boot Repair on freshly installed UEFI Windows 10 and UEFI Ubuntu 18"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by raychang on 2019-09-19
I freshly installed **UEFI Windows 10** and **UEFI Ubuntu 18.04** in a **GPT** hard disk, and then try a test run the **"Boot Repair"** 64-bit from sourceforge (latest version, 2017/10/29). It said *[COLOR=#000080]"The current session is in Legacy mode. Please  reboot the computer, and use this software in an EFI session. This will  enable this feature. For example, use a live-USB of  Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")), after making sure your BIOS is set up to boot USB in EFI mode."[/COLOR]*[COLOR=#000080], then abort.

When I try to boot the "Boot Repair Disk", my ASRock B450M Pro4 motherboard using AMD Ryzen 2600 CPU  only show the "AHCI CD ROM" in **"boot menu"**, unlike the Windows 10 or Ubuntu 18.04 install CDs. When I inserted the "Windows 10" or Ubuntu 18.04 DVD, the motherboard's "boot menu" has two options for each of them, one is "UEFI CD ROM", the other is "AHCI CD ROM". I install Windows 10 and Ubuntu 18.04 both by choosing [/COLOR][COLOR=#000080][COLOR=#000080]UEFI CD ROM" to boot to install. [/COLOR]However, when I inserted the boot repair Disk, the motherboard's "Boot Menu" only show "AHCI CD ROM", there is no "UEFI CD ROM" option. I also try to flash a bootable USB pen drive for "Boot Repair", the same thing happened, I cannot boot it into UEFI mode. If there is a way to boot this "Boot Repair" disk into UEFI mode, I'd like to do so, but it seemed to me that the disk itself does not provide that option to my motherboard to recognize the other option. if I disable the CSM mode in UEFI setup to force the PC to use **UEFI only**, it will not even show the boot option for CD ROM in "Boot Menu" when I inserted the "Boot repair Disk". As I mentioned, Windows 10 and Ubuntu 18.04 both have that "UEFI CD ROM" option in "Boot Menu"  I am not sure if it only happened to my motherboard or else. Does any other users have similar problems? For people that have successfully use "Boot Repair" disk, how did you make it boot under UEFI mode?

Thanks.

[/COLOR]

---

### Post by oldfred on 2019-09-19
Do not use Boot-Repair ISO, it is old. It still should offer to boot in UEFI mode. Also better to get software directly from source, rather than third party.
Perhaps your B450 is too new as needs the newer kernel & drivers in the latest Ubuntu.

Use your Ubuntu live installer and add Boot-Repair to it.

Many newer UEFI systems also need UEFI update. Are you running latest UEFI from Asrock?
And if SSD, it may also need firmware update.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by raychang on 2019-09-20
> **oldfred said:**
> 
Use your Ubuntu live installer and add Boot-Repair to it.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO

Thanks, the 2nd option works! I am wondering if there is a way to make a new Boot Repair Disk by first boot into UEFI Live Cd then install the BootRepair (2nd Option), then somehow save the live CD session with installed Boot-Repair into a ew Boot Repair disk? I am worry about the situation when I lost internet connection after booting into Live CD.

Thanks.

---

### Post by oldfred on 2019-09-21
You can create a live installer with persistence. 
I prefer to just do a full install to flash drive, but more difficult as Ubuntu's Ubiquity installer only wants to install grub to internal drive. Several work arounds.

Most just create a live installer with persistence. It will not let you keep Boot-Repair installed, but you save it to the save data partition that you add to flash drive.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[URL="http://ubuntuforums.org/showthread.php?t=1655412"]http://ubuntuforums.org/showthread.php?t=1655412
      [/URL]
 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) 
    
Edit ISO in place:
[https://ubuntuforums.org/showthread.php?t=2426728](https://ubuntuforums.org/showthread.php?t=2426728)

---

