---
title: "Installing ubuntu 19.04 on second hard drive while keeping original dual-boot install"
date: 2019-04-29
forum: Installation &amp; Upgrades
---

### Post by joebuntu99 on 2019-04-29
Greetings!

I have been happily using Ubuntustudio 18.04 dual-booting with Windows 10 Pro on my laptop hdd.

I have (sucessfully) installed a M.2 SSD in addition to my main drive.

I wish to install Ubuntustudio 19.04 on my new ssd while keeping my other two operating systems on my main hdd for now.

I boot the ubuntustudio 19.04 installer on a usb stick.
When asked to choose type of install I choose "Do something else".
I choose the M.2 SSD.

The other option is to choose "where to install the boot loader". Which drive should I choose? The original hdd or the new target ssd?

Will I be able to choose from my three operating systems (ubuntu 18.04, ubuntu 19.04 and windows 10) from the Grub screen as I can choose from my two operating systems (18.04 and windows 10) now?

Thank you in advance for you help and advice

Kind regards
Joe

---

### Post by oldfred on 2019-04-29
Are Windows & current install UEFI or BIOS?
Yes, grub will boot all systems, if you install system in same boot mode as current installs.
But only one ubuntu entry will be in UEFI boot menu, grub after update will include every install in same boot mode.

I prefer to partition in advance & use gpt. And include an ESP - efi system partition on SSD. It may not be used as grub only wants to install to first drive, often sda or first NVMe. But if it does install to SSD, it may erase the UEFI entry even though that was/is still valid UEFI entry. Just happens to have same 'ubuntu' label.
In gparted before anything else, change from default MBR/msdos to gpt.

If drive is NVMe type or seen as sda, grub may want to install to it and will error out if you do not have an ESP on it. 
I just installed 19.04 on sdb with main working install 18.04 on sda which is SSD. Even though I specified to install grub to sdb, it only installed to sda, overwriting default grub boot to 18.04. I had to boot into 18.04 from 19.04's grub menu and edit my /EFI/ubuntu/grub.cfg to use 18.04's UUID to be default boot.

After install, run Boot-Repair and post link to its summary report.
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

### Post by joebuntu99 on 2019-05-01
UEFI as a replacement for BIOS was something I was unaware of but after some research it turns my Ubuntu 18.04 & Windows 10 Pro were booting with Legacy BIOS system. I decided to use GPT and EFI for my new install so I prepared my new SSD on /dev/sdb with a GPT partition table and an EFI boot partition on /dev/sdb1. In my laptop (Thinkpad X250) Firmware Setup (what I would have called the bios) I switched boot mode to UEFI with legacy support. I installed ubuntustudio 19.04 to my ssd on /dev/sdb2 and instructed the installer to place the boot loader on /dev/sdb1.

The installation was successful. Grub (a newer looking interface) gave me the option of booting "Ubuntu" or "Ubuntu 18.04 (on /dev/sda5)" but no option to boot windows.
I changed the boot mode in the firmware setup menu to mixed UEFI & Legacy with UEFI first but still no option to boot windows.
I changed boot mode to Legacy only and the original grub menu loaded giving me the option of booting Ubuntu 18.04 or Windows 10.
This suits me fine for now as Windows is not often required so I can put the laptop in UEFI boot mode with legacy support and use either of my ubuntu installs and when I need windows I can simply change the boot mode to access it through the older grub menu. In the future I will replace the drive on /dev/sda with an ssd and ensure everything is booting with UEFI.

Not being able to leave well enough alone however I ran boot-repair from ubuntu 19.04.
The report can be found here [http://paste.ubuntu.com/p/KY2dFW2RyT/](http://paste.ubuntu.com/p/KY2dFW2RyT/)

The result here is some additional options in the "19.04 Grub" menu.
These seem to be items stored in the EFI partition on sdb1.
EFI/BOOT/bkotbiitx64.efi
EFI/BOOT/fbx64.efi
EFI/BOOT/mmx64.efi
EFI/ubuntu/mmx64.efi
The first two item seemingly do nothing when selected - I just return to grub.
The second two load some utility I am unfamiliar with but also bring me back to grub.
I can still boot to ubuntu 19.04 and 18.04 from the grub menu. And I can still boot to ubuntu 18.04 or Windows from the "18.04 grub menu" when I switch boot mode to legacy.

It would be nice to remove those four items from the grub menu for aesthetic reasons.
It would be nice to be able to boot to windows from the "19.04 grub menu" but I am not too bothered about that - it may not even be possible?

Joe

---

### Post by oldfred on 2019-05-01
UEFI and BIOS are not compatible.
They write hardware info differently to hard drive for operating system to use. Once you start booting in one mode you cannot switch. Or from grub you can only boot other installs that are in same mode.
UEFI has a one time boot, and some boot loaders will some how use the one time total reboot into the other system that is in different boot mode. But usually easier just to choose that from UEFI boot menu.
While some systems require you to turn on/off UEFI or legacy boot mode, most now will boot correctly in mode installed from UEFI boot menu.

Your UEFI shows a Windows UEFI boot entry, but your Windows is installed in BIOS boot mode. Did you reinstall Windows on sda?
Windows only boots in BIOS mode from MBR partitioned drives and only boots in UEFI mode from gpt partitioned drives.

Some instructions on housecleaning some grub entries, UEFI entries are in link in my signature.
Boot-Repair likes to add a 25_custom for other .efi boot files found. I have multiple installs some obsolete, so I turn off os-prober and add just the boot stanzas for the installs I want in 40_custom.

---

### Post by joebuntu99 on 2019-05-02
I am happy with the current state of my system while I migrate to a more modern setup with SSDs and pure UEFI booting. So I shall mark the thread as solved. Thank you.

---

