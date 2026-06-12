---
title: "How to install Ubuntu 10.10 on Usb"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by ivan1500 on 2010-12-08
Hello i am new to Ubuntu/Linux and i want to know how to install Ubuntu 10.10 On Usb.
But i don't like Live Usb i want full instalation of ubuntu on my usb and i want to install programs and applications on it, with the live usb i can't install programs :( .
I want the easiest way to install full Ubuntu on Usb because I am a beginner in this.:D
I have 4Gb TakeMS Usb

---

### Post by sikander3786 on 2010-12-08
Welcome to the forums :-)

Boot from an Ubuntu disc, plug in your USB and use Startup Disk Creator found under System > Administration menu to do a persistent install.

Or you can also install Ubuntu to the USB just as you'd install it to an internal HDD. Disconnect all internal HDDs so that Grub (the Ubuntu bootloader) doesn't mess up your existing installs.

See method # 1 or more options here.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

We also have an expert on USB installs. They might be here soon ;-)

---

### Post by Harsh Kumar Narula on 2010-12-08
Or You can use **UNETBOOTIN** as well.. This also works very neatly and beautifully. Its there in the software repositories of Maverick .

---

### Post by sikander3786 on 2010-12-08
> **Harsh Kumar Narula said:**
> Or You can use **UNETBOOTIN** as well.. This also works very neatly and beautifully. Its there in the software repositories of Maverick .
That doesn't have an option for persistent install by default.

However, it can be made persistent. See this.

courtesy of forum member **C.S.Cameron**
[http://ubuntuforums.org/showpost.php?p=9756662&postcount=4](http://ubuntuforums.org/showpost.php?p=9756662&postcount=4)

---

### Post by Harsh Kumar Narula on 2010-12-08
Thanks Sikandar for adding.... :)

---

### Post by ivan1500 on 2010-12-08
I install from the tutorial in pendrivelinux and now i cant install programs on ubuntu when i try to install from terminal!
How to solve this problem pleas help me.

---

### Post by C.S.Cameron on 2010-12-09
Step by step for full install of 10.10:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by Sef on 2010-12-09
An easy way to create a live usb is to follow the [directions]("http://www.ubuntu.com/desktop/get-ubuntu/download") on ubuntu.com, then go to number 2.

---

### Post by C.S.Cameron on 2010-12-09
forgive me if I am wrong, but I understood that Ivan asked for simple instructi0ons for a full install, not a persistent one.
A persistent install is ok for test driving Ubuntu, it's faster than the Live CD.
A full install is better for someone who wants to learn about Ubuntu, installing drivers, customisation, compiz, etc. There is also lots of hellp in these forums from other people that are running HDD instals, more so than persistent installs.

---

### Post by ivan1500 on 2010-12-09
^^^ Yes that is it i want FULL installation on my usb and i want easy way if there is not easy way than pleas post the hard way I will[COLOR=#000000] try to install
[/COLOR]

---

### Post by Bo0ddha on 2010-12-09
I think I was JUST about to ask this question. I want to make sure I understand.  I have a netbook and I want to run ubuntu on it without dual booting it.  I ONLY have the netbook at the moment to install from.  It's going to be used by my wife also for classes and such and don't want to take any chances messing things up while I'm learning.  Is this persistent install using the usb drive as the hard drive to run everything from?  Whatever I install/update/save will be saved onto the usb drive?  It's not a live demo version that is only temporary?  I can take it from computer to computer and use it?  Does it mess with the boot loader at all?

---

### Post by C.S.Cameron on 2010-12-09
> **ivan1500 said:**
> ^^^ Yes that is it i want FULL installation on my usb and i want easy way if there is not easy way than pleas post the hard way I will[COLOR=#000000] try to install
[/COLOR]

See post #7 above for a step by step method of Full install to USB drive.
If you want it simpler do not make the optional partitions.

---

### Post by C.S.Cameron on 2010-12-09
> **Bo0ddha said:**
> I think I was JUST about to ask this question. I want to make sure I understand.  I have a netbook and I want to run ubuntu on it without dual booting it.  I ONLY have the netbook at the moment to install from.  It's going to be used by my wife also for classes and such and don't want to take any chances messing things up while I'm learning.  Is this persistent install using the usb drive as the hard drive to run everything from?  Whatever I install/update/save will be saved onto the usb drive?  It's not a live demo version that is only temporary?  I can take it from computer to computer and use it?  Does it mess with the boot loader at all?


It sounds like a persistent install using usb-creator as in post #2 above will work for you, It is pretty hard to mess anything up doing one.
Persistence is limited to 4GB out of the box, (it can be made larger using a casper-rw partition). A few other things don't work that do with a Full install.
It is a great method for doing a test drive. I use a persistent UNetbootin install on my 4GB EEE PC.

---

### Post by amtzone on 2010-12-09
using this _**[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)**_....it been provided in the download section of ubuntu.....;)

---

### Post by Bo0ddha on 2010-12-10
> **C.S.Cameron said:**
> It sounds like a persistent install using usb-creator as in post #2 above will work for you, It is pretty hard to mess anything up doing one.
Persistence is limited to 4GB out of the box, (it can be made larger using a casper-rw partition). A few other things don't work that do with a Full install.
It is a great method for doing a test drive. I use a persistent UNetbootin install on my 4GB EEE PC.

Can this also be done using a USB hdd partition?  I know the utility on pendrivelinux does not find the formatted partition on a external hdd.  I've been trying.  Can't get to my usb sticks for another month when I get home.  Only have my external usb hdd.

---

### Post by C.S.Cameron on 2010-12-10
> **Bo0ddha said:**
> Can this also be done using a USB hdd partition?  I know the utility on pendrivelinux does not find the formatted partition on a external hdd.  I've been trying.  Can't get to my usb sticks for another month when I get home.  Only have my external usb hdd.

Usb-creator from the Live CD will work with an external USB HDD.

---

### Post by Bo0ddha on 2010-12-10
> **C.S.Cameron said:**
> Step by step for full install of 10.10:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

First thanks for all the help.  Grabbed a cheap usb drive and got that working just fine.  Interested in doing the above to my usb hdd.  I'm on a netbook.  Rather not really unplug the internal hdd.  Planning on booting into ubuntu from the flash drive and following your directions to install it to the hdd.  Now if I follow your directions (minus unpluging the internal drive and skipping adding the windows partition since it already has some ntfs partitions) the boot loader will be installed to the EXTERNAL hdd and not the original mbr?

Edit: realized I left something out.  I would want to put regular ubuntu onto the usb hdd from my netbook.

---

### Post by C.S.Cameron on 2010-12-10
I would leave the NTFS as the first partition, best to defrag before proceeding.
Once you are in manual partitioning
> (Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Installing from a flash drive and leaving the internal HDD plugged in you may find that both drives are listed in the external HDD's grub.
This may suit you as you can leave your external drive plugged in and still boot the internal drive by selecting it from the grub menu.
If you want to get rid of the reference to the flash drive in grub just run "update-grub" with it removed.

---

### Post by Bo0ddha on 2010-12-11
Thank you so much for all of your patience.  My USB drive is working fantastically.  Installing to the hdd now.  So far I absolutely love using ubuntu.  Always played around in the past, but I think I might make it my main OS now.  Especially since I can have a hdd that holds it all by itself.

---

### Post by ivan1500 on 2010-12-12
Ok can someone to help me to install ubuntu 10.10 on my usb(4gb) and i want full installation on my usb no live no Persistent i want FULL pleas post same tutorial step by step to install Full ubuntu 10.10 on my 4gb Usb

---

### Post by C.S.Cameron on 2010-12-12
> **ivan1500 said:**
> Ok can someone to help me to install ubuntu 10.10 on my usb(4gb) and i want full installation on my usb no live no Persistent i want FULL pleas post same tutorial step by step to install Full ubuntu 10.10 on my 4gb Usb

Do you not like the method posted above?
It seems to have worked for Bo0ddha.
You can leave out the optional partitions if you want something simple.
Thus making your / partition 4GB.
If you can unplug your internal hard drive you do not even need to use manual partitioning.

---

### Post by ivan1500 on 2010-12-12
^^^Thank you man i solved the problem i just install full ubuntu on my usb and now i am on it :D

Thank you man thank you

---

