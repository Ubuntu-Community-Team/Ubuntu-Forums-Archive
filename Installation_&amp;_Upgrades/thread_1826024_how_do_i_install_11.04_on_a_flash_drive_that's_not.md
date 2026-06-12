---
title: "how do i install 11.04 on a flash drive that's not live persistent mode?"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by LeadHop on 2011-08-16
I've been working on this for days, and maybe I'm making it more complicated than necessary. 

I recently got a 16gb nano flash drive and thought it'd be awesome to move my entire linux install to there as to boot from different machines.

I've found loads of resources on creating a live disk with a persistent file but my impression was that not only is that slower, but I'd also rather not deal with the boot menu of "run w/o install, install w/o boot" etc. every time I boot as ubuntu is my primary OS.

I've found several resources, all of which are focused towards the live persistent or older versions (note: older versions would be ok if they could be upgraded to 11.04 from the USB).  I've tried installing 11.04 several times to the blank 16gb from one live USB to the blank 16gb but the machine freezes up at a black screen with a blinking cursor on the top left hand when booting from the newly installed USB drive.  The resources I can find also all resort to fat32 formatting (i'd prefer ext4 as I do have some larger files I'd like to have on the drive).  

I've also tried installing grub2 to the 16gb after 11.04 was installed to no avail.

This does all sound finicky but it's something I've always wanted.  Right now i'm thinking about settling for colinux:

[http://www.pendrivelinux.com/colinux-portable-ubuntu-for-windows/](http://www.pendrivelinux.com/colinux-portable-ubuntu-for-windows/)

which is not ideal, but I'd be willing to try if all the catalogs were available as it is to regular ubuntu 11.04.

Is this possible or am i trying to have my cake and eat it too?  TIA!

---

### Post by garvinrick4 on 2011-08-16
Should be able to make a partition in ext3 or ext4, if drive is sdb then partition would
be sdb1 and a swap as sdb2. In gparted and regular install using manual install and / as mount point and grub installed in sdb and then should boot fine when Usb choosen in BIOS to boot first. When grub updated will boot whatever is on sda also. Operating System does not care as long as has a mbr, usb flash drives do. Could just install as use whole drive and make sure you choose sdb or flash drive. Could be sdc or sdd according to how many drives installed.

---

### Post by spcwingo on 2011-08-16
You could use remastersys in backup mode to create a live disc image of your install (be aware that this will be ALL of your data including saved passwords, etc.) then use unetbootin to create a live USB stick from the disc image.

---

### Post by LeadHop on 2011-08-18
#2 - that's what I've been attempting several times but I'm having difficulty getting grub installed on the drive.  I'm not sure why.

#3 - so close!  that sounds like it would be perfect if I could just get the flash to boot!

---

### Post by garvinrick4 on 2011-08-18
So you have a live cd of 11.04?
boot off of it and then put usb flash in.
It will be mounted in media lets say you open file system look in /media and it says it is
centon_flash I will use that for this use your own.
[COLOR=Red]It is already mounted so run:[/COLOR]
sudo fdisk -l (lower case L)
see what sd# your flash drive is lets say sdb for this. Use your own:
```
sudo grub-install --boot-directory=/media/centon_flash/boot  /dev/sdb
sudo umount /media/centon_flash
sudo reboot
```Now take out your cd: 
[COLOR=Red]###Make your USB is set to boot before the HDD in Bios.[/COLOR]

10.10 use this line of code because a different version of grub 1.98 below and above is 1.99(11.04 and 11.10)
```
grub-install -v
``` (gives you version)
below use this line for 1.98 for grub install to mbr (master boot record)
```
sudo grub-install --root-directory=/media/centon_flash /dev/sdb
```

---

### Post by LeadHop on 2011-09-19
The first code works but it has no affect on the booting process... which means I can't boot into the USB to input the grub install code.  I'm still facing a black screen with a blinking cursor in the top left.  Is there no way to make a bootable installation on a USB drive that's not a persistent/live mode?

---

### Post by raja.genupula on 2011-09-19
hey man
i hope this link can help you 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by LeadHop on 2011-09-20
Thanks - I appreciate the input but it looks like thats instructions for installing a live persistent mode on the USB.  I'd prefer to avoid that since I heard the live persistent mode tends to run slower than a regular install.  

I also tried loading the bootloader on to the USB to no success.  I'm not sure if those instructions are valid anymore on newer distros. 

Is it that there's just no way to put a full install that's not a live persistent mode on to a USB?  It seems like it should be doable.

---

### Post by fresnofred on 2011-11-18
I just install Ubuntu directly to the flash drive!  But to avoid complications, I disconnect the hard drive first, then boot to the live cd and then just do a regular install.  Ubuntu should only find the flash drive this way and not cause boot problems like can occur if the hard drive is listed (not listed as it has been disconnected)

---

### Post by fredbird67 on 2011-12-07
FresnoFred, I tried that once with CrunchBang, and it was SLOW!  Don't know whether it's also slow with Ubuntu, though...

---

### Post by C.S.Cameron on 2011-12-07
Following step by step for Full install of 11.04 to USB device, partition sizes given are for 8GB drive, adjust size to suit.
There are many posts describing how to move an existing home folder to a new install:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
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
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

### Post by Montezuma45 on 2011-12-08
Check out Unetbootin for being able to boot from the Flash drive and having the Live version.

---

