---
title: "How to do full install to an external HDD?"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by Anthony A on 2011-01-30
Is there a way to install Ubuntu to an external HDD so I can  boot from it on different computers?

I already use the live CD on a USB stick. I used Universal USB Installer and this makes Ubuntu persistent but I want a full install that I can update and not have the size limits that the live CD/USB have.

Thanks

---

### Post by presence1960 on 2011-01-30
Install Ubuntu to the external HDD. make sure you designate GRUB to go on the MBR of the ext HDD. For example if you have one internal disk and the external disk, your external most likely will be sdb. So make GRUB go to sdb. **_Do not put it on the boot sector of a partition such as sdb1_**

Just make sure you designate it to go to the correct disk's MBR. Then to boot it on other machines you just need to set BIOS to boot from that external disk before anything else.

---

### Post by Anthony A on 2011-01-30
> **presence1960 said:**
> Install Ubuntu to the external HDD. make sure you designate GRUB to go on the MBR of the ext HDD. For example if you have one internal disk and the external disk, your external most likely will be sdb. So make GRUB go to sdb. **_Do not put it on the boot sector of a partition such as sdb1_**

Just make sure you designate it to go to the correct disk's MBR. Then to boot it on other machines you just need to set BIOS to boot from that external disk before anything else.

OK thanks I will give that a try. 

I read some where else that physically removing the internal HDD and than booting from the live CD/USB to do the install while the external HDD is connected makes Ubuntu install to the external HDD automatically since it has no other option. Is this a good idea?

---

### Post by presence1960 on 2011-01-30
If you are not confident about what you are about to do, then disconnect the internal disk. It is not necessary though.

---

### Post by C.S.Cameron on 2011-01-30
Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
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
"Use as:" = "NTFS file system"
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

### Post by Anthony A on 2011-01-31
Wow thats much more involved than I thought. Thanks for the info.

---

### Post by Anthony A on 2011-02-08
OK, I did a default install to an external HDD and removed the internal drive while I did this. The install finished with no problems and I can boot off the external HDD no problem and Ubuntu runs well.

I am having a problem with sleep/standby though. The computer will sleep/standby no problem when I close the lid or select standby from the options. The problem is waking from standby. When I open the lid everything appears to be waking from standby, some text flashes across the screen and then all I have is a black screen and a cursor. The cursor moves around just fine and the machine is clearly running and not in standby but I have a black screen. I have to force a shut down and reboot to get Ubuntu running.

Any suggestions on whats happening and how to fix this?  Thanks

---

### Post by Anthony A on 2011-02-08
I have been Googeling for hours and have not found a similar problem. Most have problems booting from the HDD, not coming out of standby.

---

