---
title: "want to create a few usb boot drives but don't want to interfere with windows"
date: 2016-11-04
forum: Installation &amp; Upgrades
---

### Post by intertan on 2016-11-04
I would like to create 4-5 usb sticks I can boot Ubuntu from and have persistance.
due to the nature of what is going to happen I will start with 64bit 16.10 then eventually got to server as I am more into the processing power of the cpu than anything,


Problem is I don't want windows to be affected at all. when my machine boots up it boots as normal unless I have the usb drive in and select boot from usb.

Is there a guide or program to use in windows to set this up?
I do  have an older laptop to use to ensure I don't affect the boot manager.

---

### Post by alexjpowell on 2016-11-04
What you're after sounds like an Ubuntu live CD, but installed onto a memory stick
GRUB won't be installed, shouldn't be installed- you just need to select "Try Ubuntu" when you boot into it and space permitting you will be able to install whatever you want on there

[https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by sudodus on 2016-11-04
Welcome to the Ubuntu Forums :-)

Maybe it would work for you along these lines:

1. Find out how to select boot drive via a hotkey (maybe Esc, F2, F9, F10, F12 or Enter, it is different between computers). After pressing that key you should get a menu, where you can select your USB stick.

This will not affect the automatic booting into Windows (unless you run in UEFI mode and have to turn off secure boot).

2. Create a persistent live system on your USB sticks. I suggest that you try mkusb according to these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

3. If there are still problems, you can read the tips in the following link (and links from it)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

4. And it will be easier for us to help you, if you tell us as much as possible about your computer, at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by gordintoronto on 2016-11-05
If you have an older laptop, you might have a better experience by using Xubuntu or Ubuntu Mate.

Pendrive linux can create a bootable flash drive with persistence from Windows. If you set the BIOS to boot first from USB, then from the hard drive, it should produce the result you want, without having to take any action at boot time, other than plugging or unplugging the flash drive.

A different approach is to burn a Live DVD with Linux, boot from it, and *install* onto a flash drive. The downside is that if you don't know what you are doing, you will wipe out Windows. Having an image backup of Windows is always a good idea; Macrium Reflect has a free version which can produce this.

---

### Post by C.S.Cameron on 2016-11-05
It sounds like you might prefer Full installs to Persistent ones, (however, if you do prefer Persistent installs mkusb is the way to go, not sure if it does Server). 
For a Full install of Ubuntu you need at least an 8GB flash drive, preferably USB3.
I would recommend unplugging the internal drive during the install, that way you can't mess it up.
You can then install to flash drive the same as to internal drive.
If you do want to enter grub when booting you can do an update-grub later with all drives plugged in.
You will probably want to use "something else" during partitioning if you ever plan on using the flash drive for info transfer to a Windows computer.
The first partition should be FAT32 or NTFS.
If you do make a persistent install check that automatic updates is turned off, they can quickly fill the drive and it will then not boot.

---

