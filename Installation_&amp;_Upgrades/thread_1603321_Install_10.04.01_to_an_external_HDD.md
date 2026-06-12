---
title: "Install 10.04.01 to an external HDD"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by danemaslen on 2010-10-22
I'm quite embarrassed to be asking this as I'm sure the answer must be fairly straightforward and already present somewhere in one of the threads, but unfortunately all I seem to be able to find are rather more complicated scenarios!

I currently have two PCs, namely a desktop running 8.04 and a netbook running 9.10.  I would like to install 10.04.01 onto an external USB HDD (its current contents can be zapped) and then boot from it to try out 10.04.01 on both the desktop and netbook before taking the plunge of actually upgrading them.

For the moment let's take it for granted that both the desktop and the netbook can boot from external USB hard drives.  They are both modern systems (2 years old and 1 month old respectively), so I'm assuming that this will be the case.

Can anyone point me in the direction of instructions for doing this?  I have rummaged around on help.ubuntu.com, but without success (or at least without feeling confident that I've found the right instructions).  I do of course want to avoid accidentally zapping the existing 8.04 and 9.10 systems so I'm very wary of proceeding until I'm sure I understand what I'm doing. 

Thanks.

---

### Post by sikander3786 on 2010-10-22
The safest route will be to disconnect the internal HDD on any one of the systems, plug your external USB HDD, boot from an installation media and install Ubuntu just like you'd have done a regular install. Its simple. You'll have a complete install just like an internal HDD install.

If you choose not to disconnect the internal HDD, you'll need to take care of the bootloader during the installer so that it gets installed on your external HDD, not the internal one.

If you just want to test the 2 PCs with Lucid, Live CD or a Live USB will be the better option.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by C.S.Cameron on 2010-10-22
Step by step:
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
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
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
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by danemaslen on 2010-10-23
> **sikander3786 said:**
> If you just want to test the 2 PCs with Lucid, Live CD or a Live USB will be the better option.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Thanks.  I'll take a look at that option and decide whether the Live USB route will allow me to check what I want to check.

> **C.S.Cameron said:**
> Step by step:


Thanks for the detailed instructions.  I'm not a fan of messing around inside the PC, but if I stick with my original plan of installing 10.04.01 on the external hard disk, I might well go for the added security of disconnecting the internal drive on the desktop PC so that I can't make a fatal blunder!

---

