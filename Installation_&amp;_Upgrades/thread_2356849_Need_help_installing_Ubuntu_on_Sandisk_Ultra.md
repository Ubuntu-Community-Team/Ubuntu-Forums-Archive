---
title: "Need help installing Ubuntu on Sandisk Ultra"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by Supersonicx10 on 2017-03-27
I need some help installing Ubuntu 16.04 on a Sandisk Ultra can anybody help me and or tell me how to do it?

---

### Post by sudodus on 2017-03-27
- How do you want to install it? 'Live-only', 'persistent live' or 'installed system'?

- In what computers do you intend to run Ubuntu from this Sandisk Ultra?

You can start by looking at this link and links from it, [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by RobGoss on 2017-03-27
Hello and welcome, this may help you with creating a Bootable USB [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Supersonicx10 on 2017-03-27
> **sudodus said:**
> - How do you want to install it? 'Live-only', 'persistent live' or 'installed system'?

- In what computers do you intend to run Ubuntu from this Sandisk Ultra?

You can start by looking at this link and links from it, [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

Well I want to create a dual-boot on my USB drive, what I'm trying to say is this I need to install Ubuntu on a USB port or should I say have it installed on a USB flash drive. I'm not going to replace Windows 10 but in turn have it run right beside it I already have a DVD disc burned with the OS ready for it to be installed all I need to do is to figure out how to I install it on a USB flash drive.

Computer in question

Lenovo ideacentre 710 Desktop

RAM: GB 8

OS: windows 10

Video Card: Nvidia GeForce GT 730

---

### Post by RobGoss on 2017-03-27
This is probable what you're looking for take a look here [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by yancek on 2017-03-27
Do you want to install Ubuntu on an actual usb hard drive or just on a pen/flash drive?  The process is basically the same.  You need to determine which drive is the drive you want to install from which you can do from the Ubuntu DVD.  If your computer has windows 10 on it, it is probably using UEFI so you need Ubuntu UEFI.  You might try reading the Ubuntu documentation on it at their site below.  Also, more details on your intentions.  Are you planning to install Ubuntu to an external usb drive which you will have permanently attaached to the machine with windows?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Supersonicx10 on 2017-03-27
> **yancek said:**
> Do you want to install Ubuntu on an actual usb hard drive or just on a pen/flash drive?  The process is basically the same.  You need to determine which drive is the drive you want to install from which you can do from the Ubuntu DVD.  If your computer has windows 10 on it, it is probably using UEFI so you need Ubuntu UEFI.  You might try reading the Ubuntu documentation on it at their site below.  Also, more details on your intentions.  Are you planning to install Ubuntu to an external usb drive which you will have permanently attaached to the machine with windows?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) Yes a USB flash drive but I might have to detached the drive after I'm done with it would that be a problem?

---

### Post by yancek on 2017-03-27
Doing a full install to a flash drive should not be a problem and removing the flash drive from the computer after using your DVD to install to the flash drive should not be a problem either.  If you have a UEFI install of windows, the Ubuntu will probably install it's EFI files to your hard drive along with the windows files there.  They would be in separate folders so it would not affect windows.

You might be able to create an EFI partition just for Ubuntu on the flash drive and install the EFI files there.  I'm not really sure about that so you might have to do a little research on it or wait for someone else more familiar with UEFI to respond.

---

### Post by Supersonicx10 on 2017-03-28
> **yancek said:**
> Doing a full install to a flash drive should not be a problem and removing the flash drive from the computer after using your DVD to install to the flash drive should not be a problem either.  If you have a UEFI install of windows, the Ubuntu will probably install it's EFI files to your hard drive along with the windows files there.  They would be in separate folders so it would not affect windows.

You might be able to create an EFI partition just for Ubuntu on the flash drive and install the EFI files there.  I'm not really sure about that so you might have to do a little research on it or wait for someone else more familiar with UEFI to respond.

Think I'll wait until someone who's familiar with UEFI comes around other than that I think I should try and install this on the flash drive. I know I have to turn off the auto detect in Windows for it to become a dual booting computer am I correct?

---

### Post by yancek on 2017-03-28
I think a safer/better method to use if you want Ubuntu on a flash drive is to do an MBR install on the flash drive and install Grub code to the MBR of the flash drive.  You would need to be familiar with the drive terminology so you get the right drives MBR.  You should then be able to select to boot it from the BIOS of that computer or another computer.

If you do an EFI install and Ubuntu can install it's EFI files on your EFI partition on the current computer with the windows EFI files, you won't be able to boot it EFI on another computer because there won't be an option and there won't be any EFI files on the flash drive.  Maybe someone can explain if or how you can create an EFI partition on the flash drive.  That will of course limit you to booting the flash on newer computers EFI capable.

Looks like you need to do a little reading or hopefully someone else will post with some answers.

---

### Post by sudodus on 2017-03-29
- Do you want Ubuntu to be persistent live (booting similar to booted from DVD but from USB and with persistence, that is, you can install programs and save files?

- Or do you want to install Ubuntu like installed into an internal drive, but in this case installed into a USB pendrive?

- And do you want to do it yourself 'more from scratch' or do you want some tool, that makes it 'more automatic'?

The methods to install are very different in these two cases. See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Supersonicx10 on 2017-03-30
> **sudodus said:**
> - Do you want Ubuntu to be persistent live (booting similar to booted from DVD but from USB and with persistence, that is, you can install programs and save files?

- Or do you want to install Ubuntu like installed into an internal drive, but in this case installed into a USB pendrive?

- And do you want to do it yourself 'more from scratch' or do you want some tool, that makes it 'more automatic'?

The methods to install are very different in these two cases. See this link and links from it,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

install Ubuntu like installed into an internal drive, but in this case installed into a USB pendrive.I'm leaning on automatic part more than the do-it-yourself method but it all depends on what I want.

---

### Post by sudodus on 2017-03-30
If you unplug the internal drive, you can install from one USB drive with a live Ubuntu system to another USB drive. This second USB drive will be treated like it were an internal drive. (After the installation you can plug in the internal drive again, and select which drive to boot via a hotkey (and a boot menu)).

- The system will be installed in the mode that the computer is booted in, UEFI or BIOS, and will only boot in the same mode, unless you add a bootloader for the other mode.

- Avoid proprietary drivers, if you want to system portable.

- Modify the system to avoid excessive wear of the USB pendrive.

-o-

Alternative: Install from a compressed image file of an already installed system, that boots in UEFI and BIOS mode. Select a mini-system with text mode interface. After installation, when booted into it, you can easily install the desktop environment of your choice, for example that of standard Ubuntu.

See this link: [help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by Supersonicx10 on 2017-04-05
> **sudodus said:**
> If you unplug the internal drive, you can install from one USB drive with a live Ubuntu system to another USB drive. This second USB drive will be treated like it were an internal drive. (After the installation you can plug in the internal drive again, and select which drive to boot via a hotkey (and a boot menu)).

- The system will be installed in the mode that the computer is booted in, UEFI or BIOS, and will only boot in the same mode, unless you add a bootloader for the other mode.

- Avoid proprietary drivers, if you want to system portable.

- Modify the system to avoid excessive wear of the USB pendrive.

-o-

Alternative: Install from a compressed image file of an already installed system, that boots in UEFI and BIOS mode. Select a mini-system with text mode interface. After installation, when booted into it, you can easily install the desktop environment of your choice, for example that of standard Ubuntu.

See this link: [help.ubuntu.com/community/Installation/UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

Well I tried to install it on the flash drive however, I use my laptop to do it. Though I was successful in doing so the only thing that kept popping up for error messages not sure what they mean though but I will take some pictures and upload them here to you guys can tell me what they mean.

[IMG]http://i.imgur.com/9xNSaSMl.jpg[/IMG]

---

### Post by sudodus on 2017-04-17
I don't know what is wrong. I hope someone else can chip in and help you.

Bump

---

