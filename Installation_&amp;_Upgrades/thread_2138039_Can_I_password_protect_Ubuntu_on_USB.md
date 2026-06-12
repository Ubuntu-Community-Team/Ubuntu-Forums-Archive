---
title: "Can I password protect Ubuntu on USB?"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by Vulpus on 2013-04-22
I have installed 12.10 on a USB pendrive and all seems to be working well, when I reboot all my saved settings are restored. However, I need to password protect the drive in case I lose it. Is there some way I can do this?

---

### Post by slickymaster on 2013-04-22
[Truecrypt]("http://www.truecrypt.org/"). With it, you can encrypt the entire drive.

Also, check out:
[Encrypted Filesystems On Removable Storage]("https://help.ubuntu.com/community/EncryptedFilesystemsOnRemovableStorage") and [TrueCrypt]("https://help.ubuntu.com/community/TrueCrypt")

---

### Post by C.S.Cameron on 2013-04-22
Yes, you can have a password for both Persistent install and Full install.
With persistent install casper-rw is easy to mount and access even with a password.
With a Full install you can choose to encrypt home during the install process.
It is just as secure as an encrypted install to internal drive.


Edit:
Except that an internal drive is probably harder to misplace.

---

### Post by nonamedotc on 2013-04-22
Or ... you can just encrypt the home directory during the installation. Although, encrypting /home would be more convenient.

---

### Post by Vulpus on 2013-04-23
Truecrypt does seem to be best option but it is a shame that Ubuntu does not have password protection built in. I previously used Saluki Linux and Knoppix on a USB and both have encryption and password protection built in. The problem is that I cannot use my Ubuntu One account very easily with either.

---

### Post by Vulpus on 2013-04-23
Well I have just tried booting in again and THIS time it asked me for my password! I had previously set up a new user complete with password but never actually got asked for it, it just booted straight in every time. Now it seems to have started working for some reason.

---

### Post by coldraven on 2013-04-23
You can switch automatic login on/off in "User Accounts"

---

### Post by Vulpus on 2013-04-23
> **coldraven said:**
> You can switch automatic login on/off in "User Accounts"

Yes, it was originally off. I think I switched it on, rebooted and then switched it off again. Only then did it ask me for the password.

---

### Post by C.S.Cameron on 2013-04-23
As I mentioned above, the password does not do much good with a persistent install as casper-rw, (the persistence file), can be easily mounted and all the information accessed.

You need to do a Full install to encrypt home.

---

### Post by Vulpus on 2013-04-23
[QUOTE=C.S.Cameron;12615505
You need to do a Full install to encrypt home.[/QUOTE]

But can you do a full install to a USB pendrive?

---

### Post by slickymaster on 2013-04-23
[Live Usb Pendrive Persistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by C.S.Cameron on 2013-04-23
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.
It is basically just like installing to internal drive:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "**Encrypt my home folder**" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can update-grub later, if you wish.

---

### Post by Vulpus on 2013-04-24
Thanks for that, I will certainly give that a go.

---

