---
title: "Boot Up with USB SSD"
date: 2020-07-21
forum: Installation &amp; Upgrades
---

### Post by christianbclark on 2020-07-21
1. I have put a fresh installment of Ubuntu 20.04 on an USB SSD. 
2. I have unplugged it. 
3. I have put a fresh installment of Windows 10 on motherboard SSD. 
4. When I want to boot up with USB SSD, I need to use F12 and select the USB SSD to boot up Ubuntu 20.04. 


Any way to just boot up, without to need to select the disk ? I have searched everywhere.

---

### Post by sudodus on 2020-07-21
Many people prefer the setup that you have (using F12 and a temporary boot menu) for this purpose.

If you want to boot into Ubuntu by default, it might be possible to change the boot order in the UEFI/BIOS system. Press a hotkey to enter the menus of the UEFI/BIOS system and try to change the boot order. I cannot help with the details, because these things are very different between computers.

If this does not work, for example because the computer always 'wants to' boot into the internal drive, then you must modify the boot system of the internal drive. so install the grub bootloader into the internal drive. This can be done manually or automatically, and is potentially risky, so you had better backup everything that you cannot afford to lose (personal files) before doing it.

Maybe the following links and links from it can help,

[help.ubuntu.com/community/Installation/FromUSBStick/bootUSB](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB)

[help.ubuntu.com/community/Installation/FromUSBStick/uefi](https://help.ubuntu.com/community/Installation/FromUSBStick/bootUSB)

[help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by C.S.Cameron on 2020-07-21
GRUB bootloader will boot both OS as long as they are both either BIOS or both UEFI mode.
Assuming that you want to retain the Windows boot loader on the internal SSD:
Boot the USB SSD and in Terminal run "sudo update-grub". Windows will be added to the USB's boot menu.
Set the USB SSD to boot before the internal SSD.
GRUB will give you a choice to boot Ubuntu or Windows

---

### Post by abertomeu on 2020-07-21
I also plan to install Ubuntu on a USB 3.1 SSD. 
Is it pretty straight-forward? I found a tutorial on youtube but the vlogger is instructing us to remove the internal drive of the computer so that Windows wont get in the way of installing on the external drive. 
Sounds overkill to me.

---

### Post by oldfred on 2020-07-21
Issue is Ubuntu's Ubiquity installer and a very old bug.
Other distributions let you choose where to install grub bootloader, Ubiquity has the choices, but they only work for old BIOS based installs.

You do not necessarily have to physically disconnect drive, but often can logically disable drive in UEFI settings temporarily.

If you do not want or are not able to disconnect drive, you have at least a couple of work arounds.
Default install will install grub to first drive's ESP - efi system partition, sharing with Windows but in separate folder /EFI/ubuntu. You can then boot the UEFI entry in the internal drive to boot install on external. But external will only work on this one system, not any others as it has no boot files. And if grub is default boot, when drive disconnected you just get a grub error as it cannot find rest of grub in the missing drive.

You can partition in advance to make sure you have an ESP on external drive and just reinstall grub. Often easier with Boot-Repair, but you can just reinstall from inside the install.

Or you can do this work around during install to change default ESP & then edit fstab with correct UUID for ESP.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by sudodus on 2020-07-21
@christianbclark and @abertomeu,

If you need not encrypt the drive, there is an easy alternative. You can use a compressed image of an installed Ubuntu 20.04 LTS system: [dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz). Download, extract and clone it to your USB drive. Check it with the md5sum in [this link](https://phillw.net/isos/linux-tools/uefi-n-bios/md5sum.txt.asc).

You can extract and clone it (in one step)

- with [mkusb](https://help.ubuntu.com/community/mkusb) in Ubuntu
- with [Rufus](https://rufus.ie) in Windows (if you also have installed a program that can extract from the compressed xz format, for example **7-zip**)

After that (when booted into another drive, e.g. an Ubuntu live USB drive), you can grow the root partition with **gparted** so that it uses the whole drive, or maybe leave part of the drive and use it for a data partition with the NTFS file system for exchange of data with Windows.

See this link for more details: [help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[hr][/hr]
Edit: This installed system is installed with one user ID:

user: **guru**
password: **changeme**

The password wants *you* to change it ;-)

---

### Post by C.S.Cameron on 2020-07-22
+1
Easiest way to install to an external drive.
No need to worry about UEFI or BIOS.
[https://askubuntu.com/questions/1255783/cannot-install-ubuntu-on-my-flash-drive/1255893#1255893](https://askubuntu.com/questions/1255783/cannot-install-ubuntu-on-my-flash-drive/1255893#1255893)

---

