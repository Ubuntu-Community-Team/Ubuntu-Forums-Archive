---
title: "Black Screen Issue During Installation from Ubuntu bootable USB"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2014-02-08
_**Environment**_: 
- MSI GE60 with Nvidia GTX 765M and pre-installed Windows 8 (that I'm trying to get rid of)
- Inside BIOS: 
1) Secure Boot disabled
                    2) Fast Boot disabled  
                    3) Boot mode UEFI with CSM 
- Ubuntu 13.10 64 bits on bootable USB, made with Rufus 1.4.3: MBR with BIOS/UEFI

Hello everyone,
When I boot from the USB stick, I choose 'Install Ubuntu' from menu and ... black screen

I had the feeling this issue has something to do with the fact that the latest Nvidia Graphics drivers are not provided on the bootable Ubuntu:

1) If I modify the file \boot\grub\grub.cfg to insert 'nomodeset' before 'quiet splash' and select option 2) during the boot, I get the same result: black screen.
2) I heard about '**Melchior**' which is supposed to be able to customize the bootable Ubuntu, but I was unable to locate it on the Internet.

How can I install Nvidia drivers on the USB stick and make them installed with Ubuntu?
Or maybe someone has another solution?

---

### Post by Saravji on 2014-02-08
Hey,

had the same problem earlier today.
What worked for me:
On the startup screen, select "install ubuntu", then go into the uptions / command line / parameters.
On the line that calls vmlinuz, add " acpi_backlight=vendor" to the end of the line.
Hope this helps,

---

### Post by actionmystique on 2014-02-08
[COLOR=#000000]" acpi_backlight=vendor" did not work for my configuration.[/COLOR]

---

### Post by sudodus on 2014-02-11
> **actionmystique said:**
> _**Environment**_: 
- MSI GE60 with Nvidia GTX 765M and pre-installed Windows 8 (that I'm trying to get rid of)
- Inside BIOS: 
1) Secure Boot disabled
                    2) Fast Boot disabled  
                    3) Boot mode UEFI with CSM

- Are you intending to dual boot with Windows or overwrite Windows?
 - Is it correct that you run in UEFI mode? (I think you need that to use Windows 8)
- You may need to stop Windows from 'semi-hibernating' too.
> 
- Ubuntu 13.10 64 bits on bootable USB, made with Rufus 1.4.3: MBR with BIOS/UEFI

Can you install Ubuntu in UEFI mode (with GPT partition table, *not* MSDOS partitions with MBR)? Maybe you need another method to make the USB drive, for example cloning the iso with ***mkusb*** according to the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")
> 
I had the feeling this issue has something to do with the fact that the latest Nvidia Graphics drivers are not provided on the bootable Ubuntu:

Could be. Maybe you have to test a few proprietary drivers before you find one that works.
> 

1) If I modify the file /boot/grub/grub.cfg to insert 'nomodeset' before 'quiet splash' and select option 2) during the boot, I get the same result: black screen.
2) I heard about '**Melchior**' which is supposed to be able to customize the bootable Ubuntu, but I was unable to locate it on the Internet.

How can I install Nvidia drivers on the USB stick and make them installed with Ubuntu?
Or maybe someone has another solution?

I have not heard of Melchior.

You can install proprietary graphics drivers from the ***Software Center***, ***Synaptics*** or with terminal window commands. The name of the packages are

```
nvidia-current
nvidia-<some number> for example
nvidia-331
```

---

### Post by actionmystique on 2014-02-20
> **sudodus said:**
> - Are you intending to dual boot with Windows or overwrite Windows?
 - Is it correct that you run in UEFI mode? (I think you need that to use Windows 8)
- You may need to stop Windows from 'semi-hibernating' too.

Can you install Ubuntu in UEFI mode (with GPT partition table, *not* MSDOS partitions with MBR)? Maybe you need another method to make the USB drive, for example cloning the iso with ***mkusb*** according to the [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Could be. Maybe you have to test a few proprietary drivers before you find one that works.

I have not heard of Melchior.

You can install proprietary graphics drivers from the ***Software Center***, ***Synaptics*** or with terminal window commands. The name of the packages are

```
nvidia-current
nvidia-<some number> for example
nvidia-331
```

Thanks for your answer and sorry for the delay.

1) I've changed a little bit my initial plans: I'd like to keep Windows 8.1 on the HD, install Ubuntu on the SSD and be able to boot from it when it is inserted without having grub on the system.
2) Windows 8 uses UEFI and I don't understand why we can't have one bootable drive with GPT (Windows 8) and another with MBR (Ubuntu): I don't have this choice in my BIOS settings.
3) I'm not using 'semi-hibernating' mode in Windows.
4) You're right, rufus does not seem to be the right method in this case. I cannot install anything on the SSD from Ubuntu: my Ubuntu runs on a VBox VM; the SSD is on USB 3.0 and I read that VBox cannot use USB 3.0, only 2.0. I might try to boot the SSD formatted with Windows 8 (GPT) and with Ubuntu ISO file on it.
5) Regarding the proprietary drivers, I have no idea how to install them.

---

### Post by sudodus on 2014-02-20
> **actionmystique said:**
> Thanks for your answer and sorry for the delay.

1) I've changed a little bit my initial plans: I'd like to keep Windows 8.1 on the HD, install Ubuntu on the SSD and be able to boot from it when it is inserted without having grub on the system.
2) Windows 8 uses UEFI and I don't understand why we can't have one bootable drive with GPT (Windows 8) and another with MBR (Ubuntu): I don't have this choice in my BIOS settings.

If I remember correctly, UEFI systems do not boot from MBR (MSDOS) partition tables. Maybe it is possble to boot into a GPT drive and then point to an operating system in an MBR partition table (but I'm afraid it won't work). What might work is to change between UEFI and old style BIOS (often called CSM) in the UEFI/BIOS menu system, and boot what is installed in either UEFI mode or BIOS mode. But if you have no such choice ... maybe you can search for it one more time.
> 
3) I'm not using 'semi-hibernating' mode in Windows.
4) You're right, rufus does not seem to be the right method in this case. I cannot install anything on the SSD from Ubuntu: my Ubuntu runs on a VBox VM; the SSD is on USB 3.0 and I read that VBox cannot use USB 3.0, only 2.0. I might try to boot the SSD formatted with Windows 8 (GPT) and with Ubuntu ISO file on it.

VirtualBox does not boot from USB at all (even if it can use USB pendrives as storage devices, they don't boot). KVM can boot from USB. I must admit that I don't understand all of your item '4'. Please explain with more details how you intend to install Ubuntu!
> 

5) Regarding the proprietary drivers, I have no idea how to install them.

You can install them from the Software Center, or with command lines. Maybe it is easiest to find which might be suitable and install using the Software Center, at least if you get some kind of graphical desktop environment.

---

### Post by actionmystique on 2014-02-20
4) I'm currently migrating from an old Windows 7 laptop with a VBox Ubuntu VM which cannot be used to install Ubuntu on the USB 3.0 SSD. 
The new laptop has a HD with Windows 8.1 on it; I'd like to install Ubuntu 13.10 on the SSD and be able to boot from it on the new laptop only. 
This should clarify the situation ;)

5) The point is I cannot install the proprietary drivers befire the ISO image has booted from the SSD.

---

### Post by sudodus on 2014-02-20
Download an ***Ubuntu 12.04.4 LTS or Ubuntu 13.10 64-bit iso file*** and check it with ***md5sum***

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

I suggest that you use Unetbootin to create a USB install pendrive from Windows. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

It is probably extra complicated to do it from Ubuntu in the the virtual machine.

Insert the USB boot drive with Ubuntu and reboot the computer (the host operating system) and change the setting in the BIOS/UEFI menus to boot from the USB install pendrive or use a hotkey to get a built in menu to chooise which device to boot from. Save and exit and continue the reboot.

When booted , 'try Ubuntu' (run it live) and get a feeling how it works. Use some boot option, if you have problems, for example with the graphics chip or wifi chip.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

When you are happy with it, install Ubuntu to the SSD and reboot. If you need install a proprietary driver, do it after the installation. You may have problems, that might be solved with tips from the following links

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair
[/URL]

---

### Post by actionmystique on 2014-02-22
All the Ubuntu bootable USB creators that I've tried (Rufus, Universal USB Installer and Unetbootin) **use grub and FAT32**.  I feel that they both prevent me from avoiding the black screen that I  keep experiencing after booting from the USB and choosing "Install  Ubuntu". The point here is that I** DO NOT need a menu to dual-boot; the choice is made by inserting the USB or not inserting it**.

I believe my system with Windows 8.1 needs a:
- **UEFI bootable USB**, and probably NTFS;
- **without grub as a bootloader**; I heard about syslinux but I couldn't find a tool to install it on the USB from Windows 8.

Any tips would be much appreciated.

---

### Post by sudodus on 2014-02-22
A boot CD/DVD/USB pendrive with Ubuntu desktop 64-bit version 12.04.4 LTS and 13.10 'as is' will boot both in UEFI and BIOS mode. At least it works for me, if I

- burn a DVD from from the iso file with ***k3b***. that you install with

```
sudo apt-get install k3b
```

- flash a USB pendrive from from the iso file with ***mkusb***, that you install and run according to this [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

Start at this link for UEFI dual boot installations [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Finally, see the following link for an overview of different methods [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by actionmystique on 2014-02-23
I successfully made a bootable USB SSD with mkusb from my old system which I turned into a dual-boot (Ubuntu 13.10 and Windows 7) device.
Unfortunately, the boot did not pass the second screen on my new Windows 8.1 system: I choose the "Try Ubuntu" option and it gets stuck on the following purple screen after loading Ubuntu I guess.

How can I install the correct Nvidia video card driver on the SSD before booting?

---

### Post by actionmystique on 2014-02-23
Another detail: **when I launch GParted from my old BIOS machine to check the SSD, I get a warning**: 
"/dev/sdb contains GPT signatures, indicating that it has a GPT table. However, **it does not have a valid fake msdos partition table**, as it should. Perhaps it was corrupted - possibly by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?"

---

### Post by sudodus on 2014-02-23
I think we are at a stage, where we need help from a person with a lot of experience, *oldfred*. If you write a post at the following thread (and link to this thread for background information) it is likely that he will see it and start helping you.
[URL="http://ubuntuforums.org/showthread.php?t=1769482"]
[Boot-Repair] Graphical tool to repair the PC boot in one click[/URL]

---

### Post by fdrake on 2014-02-23
> **actionmystique said:**
> I successfully made a bootable USB SSD with mkusb from my old system which I turned into a dual-boot (Ubuntu 13.10 and Windows 7) device.
Unfortunately, the boot did not pass the second screen on my new Windows 8.1 system: I chosose the "Try Ubuntu" option and it gets stuck on the following purple screen after loading Ubuntu I guess.

How can I install the correct Nvidia video card driver on the SSD before booting?
while booting fro the usb , highlight try ubuntu and press f6 and select nomodeset : [http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb](http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb)

---

