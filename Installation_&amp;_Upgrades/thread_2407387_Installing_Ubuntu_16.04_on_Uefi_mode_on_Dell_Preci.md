---
title: "Installing Ubuntu 16.04 on Uefi mode on Dell Precision 5820"
date: 2018-12-03
forum: Installation &amp; Upgrades
---

### Post by giobaxx on 2018-12-03
[COLOR=#000000][FONT=Roboto]I'm struggling to install Ubuntu 16.04 in a Workstation Precision 5820 

I started with Secure Boot and UEFI Enabled and no Success. 
I tried with Secure Boot Disabled and UEFI Enabled and no Success 

In both case the result is the same during the boot at certain point i have black screen with a blinking cursor on the top-left of the screen.
 The only way to boot a media to install Ubuntu in Disable both Secure Boot and UEFI. There is any things that i can to so install Ubuntu with at least UEFI enabled?[/FONT][/COLOR]

---

### Post by oldfred on 2018-12-03
Generally Dell needs UEFI update from Dell, SSD firmware update if SSD.
If nVidia you will need nomodeset boot parameter.
And Dell needs drive changed in UEFI from RAID/Intel srt to AHCI, unless you have RAID 0. But if still using Windows you have to install the AHCI driver into Windows first for it to keep working.
Dell issues are common across many models as similar UEFI used, just different options for different models.
General install instructions in link in my signature, below.

Dell UEFI Dual boot instructions using Something Else[URL="https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN"]
https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN[/URL]
 [https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
    
       Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254) 
    
        DELL Precision 5820 tower and NVMe M.2 front-panel SSD issues  Secure boot off, RAID on
[https://ubuntuforums.org/showthread.php?t=2381899](https://ubuntuforums.org/showthread.php?t=2381899) 
    [URL="https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en"]
[/URL] 
 Dell update UEFI/BIOS from Linux
[URL="https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en"]https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en
      [/URL]

---

### Post by giobaxx on 2018-12-05
We had some 5820 with and additional NVME SSD and we'll have to face it, but for the moment we're trying to install in a workstation that has only one HDD and Nvidia Card and no OS present.
The only way to make the Live DVD(os USB Stick) works disable all. For the moment i've  changed only the sata operation from RAID to AHCI but nothing has Changed. 

After booted the live CD i tried to edit the boot menu adding the parameter ***nomodeset ***after **quiet splash** but i still have the same problem.  i can enter into a terminal with CTRL-ALT-F1.....CTRL-ALT-F2...but no GUI to proceed with the installation..

I'm not so good in linux...and it's possible i made some mistake...

---

### Post by oldfred on 2018-12-05
Did you update firmware, UEFI & SSD?

---

### Post by giobaxx on 2018-12-05
the model i'm working now is without SSD, however i have downloaded the latest BIOS From Dell, but  tried booting in DOS mode but that update does not run in DOS Mode. I could try to run the bios upgrade by a Windows Live CD?

---

### Post by oldfred on 2018-12-05
My Dell is a Small form factor system & I update from UEFI.
I saved Update into my ESP which is FAT32 and what UEFI requires.
[https://www.dell.com/support/article/us/en/04/sln284433/what-is-bios-and-how-to-update-the-bios-on-your-dell-system?lang=en](https://www.dell.com/support/article/us/en/04/sln284433/what-is-bios-and-how-to-update-the-bios-on-your-dell-system?lang=en)

Also many Dell now can be updated directly from Linux.
       Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en)
Your 5820 is on the list:
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

---

### Post by giobaxx on 2018-12-05
i have updated the bios to the last version available **5820T_1.8.3 **using a Windows 10 Live, but nothing has changed, same issue. Black Screen with a blinking cursor on the top left.

Probably the only way is to disables UEFI and Using Legacy Boot....i don't know....

---

### Post by oldfred on 2018-12-05
Generally black screen is not UEFI or BIOS issue, but graphics.
If nVidia you do need nomodeset until you install nVidia graphics driver from Ubuntu repository, but also may have UEFI settings for internal or external video card. Check those settings, also.

Both of the links I have above seemed to install without major video issue to same model as yours.

---

### Post by giobaxx on 2018-12-05
I'm not a linux guru so i don't know why enabling UEFI gave us problems with the Nvidia VideoCard. However i tried to use another Videocard, still a NVIDIA but quite old and the problem is the same(even with the parameter nomodeset)

Tomorrow i will try, if i found with a GPU not Nvidia

---

### Post by giobaxx on 2018-12-06
just to update. I have installed Ubuntu Server and later added Ubuntu Deskop with the proper Nvidia Driver......same issue

---

### Post by oldfred on 2018-12-06
If you switched to an older nVidia card, you have to change nVidia drivers. And new driver does not correctly replace an old one, and must be totally purged before a new/changed nVidia driver is installed.

       If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by giobaxx on 2018-12-12
At the end the only way was disabled UEFI.

---

