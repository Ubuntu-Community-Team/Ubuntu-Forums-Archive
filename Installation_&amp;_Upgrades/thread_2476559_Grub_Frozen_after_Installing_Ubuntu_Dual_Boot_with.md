---
title: "Grub Frozen after Installing Ubuntu Dual Boot with Windows 11"
date: 2022-06-29
forum: Installation &amp; Upgrades
---

### Post by thomas-chung-25 on 2022-06-29
[LIST]
[*]I installed ubuntu off of a usb drive
[*]when trying to dual boot with windows 11, grub freezes and doesn't let me move to choose an option between ubuntu or windows
[*][https://paste.ubuntu.com/p/Vqp76XZG8R/](https://paste.ubuntu.com/p/Vqp76XZG8R/)
[*]this is what the report said - that I should reinstall grub
[/LIST]



[LIST]
[*]I have tried just fixing the error with the Recommended repair button because I'm not sure exactly how to reinstall it
[*]This is the error - [https://paste.ubuntu.com/p/YQCZcGp4vy/](https://paste.ubuntu.com/p/YQCZcGp4vy/)
[/LIST]

---

### Post by tea for one on 2022-06-29
> **thomas-chung-25 said:**
> when trying to dual boot with windows 11, grub freezes and doesn't let me move to choose an option between ubuntu or windows

Does the default OS boot without you trying to choose?
Can you try another keyboard?

---

### Post by thomas-chung-25 on 2022-06-29
The default OS boots when I switch the setting in the BIOS to prioritize window but when I set it to Ubuntu first, the GRUB screen freezes while displaying the options that I can boot.
This is on my laptop, so I can hook another keyboard up with a USB and try, but I'm not sure if that will work. Additionally, the keyboard works in every occasion for example when I try Ubuntu through a bootable USB.

---

### Post by thomas-chung-25 on 2022-06-29
[INDENT].
[/INDENT]

---

### Post by tea for one on 2022-06-29
Your laptop keyboard works everywhere except Grub - quite a rare problem.
Therefore, you cannot boot into your installed Ubuntu at all?

There is a Boot Manager utility that you can install on a USB stick.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html)

Worth investigating?

---

### Post by oldfred on 2022-06-29
Check UEFI settings.
Grub uses UEFI default driver where once booted the keyboard driver is part of Ubuntu.
You may need an UEFI setting for full USB support or allow USB boot.

Also HP does not seem to support the use of efibootmgr to change boot order. When grub is installed it uses efibootmgr to change boot order. 
Those with HP have said they have to change boot order in UEFI settings (not the UEFI boot menu). 
And some have said they had to update UEFI firmware.

Note line 56 shows Ubuntu as first. But HP seem to reset that back to Windows on reboot.
You also can see boot order as shown in report:
sudo efibootmgr -v

---

