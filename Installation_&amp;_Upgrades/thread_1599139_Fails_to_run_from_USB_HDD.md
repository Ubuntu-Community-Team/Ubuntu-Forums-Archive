---
title: "Fails to run from USB HDD"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Mossey on 2010-10-17
Hi Guys! I am new to Ubunto and would like to try it for a while before going totally live. I downloaded 10.04 32bit and the USB installer and installed it on a USB HDD it workes perfectly on my laptop. I tried the same USB drive on my main Desktop computer (intel i7 930, Gigabyte GA-X58A-UD3R MB) I select Boot to USB and get the Ubunto loading screen, but it never loads. I have tried downloading the latest 10.10 and loader in both 32 bit & 64 bit with exactly the same results. Anyone with an idea? If I do get this working how can I get programs or changes I make to Ubunto when running from the USB to remain as part of the way it runs everytime I boot.
Thanks

---

### Post by C.S.Cameron on 2010-10-17
What USB installer did you use?
Both Startup Disk Creator and Universal have Persistence options that allow you to save settings and programs.
Unetbootin does not have a persistence option but can be hacked to add one.

I would suggest doing a full install to USB HDD as you should have plenty of space.

Following is for 10.10

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

### Post by ronparent on 2010-10-17
The 'fly in the ointment' in moving a usb install from one computer to another is that when installed on one, it sometimes won't run on the other  because of some hardware difference or incompatibility. A graphics processor difference is most often the cause. But often one machine will also need some special boot parameter (I have that situation). Most causes are easily fixable but may require 'debugging' with a live cd to fix on the problem area.

---

### Post by Mossey on 2010-10-18
Thanks for the replies. Just to clarify, all of my attempts to get Ubunto to run from a USB HDD on my desktop computer, the install to USB was done on the desktop computer. I have tried both 1.8.0.5 & 1.8.0.2 universal USB installers. I am not having a problem booting from the USB drive, that works fine it just loads the Ubunto screen with the dots below and stays like that forever. I did not understand what that presistance option meant so I selected nothing. I am using a Scandisk Cruzer 8GB pendrive for the install. I have many options for the install but am paranoid about it interfering with my current Win 7 64 bit OS that I am accustomed to for so many applications. My main boot drive is an 128GB SSD with a second 1TB SATA 3 drive for storage. I have a external 2.5" 250GB USB drive or a 500 GB external eSATA drive or a 4TB NAS running on my network. Maybe one of you experts could point me in a better direction to install Ubunto. I would love to learn and adapt to this type of freeware so Microsoft 2 year cash grab would be history.

---

### Post by efflandt on 2010-10-18
If you can boot an older Ubuntu version from CD or USB, see what **sudo lspci -v** shows for the video device on the problem PC.

Many people seem to have trouble booting 10.10 to a blank screen, but not sure if that is video related or that they try to create the bootable USB live/install iso with something that does not properly deal with the new syslinux yet.

---

### Post by Mossey on 2010-10-18
Sorry! Can't boot any version from a USB drive on the desktop computer in question.

---

### Post by ronparent on 2010-10-18
Delete 'quiet splash' from your boot line. This will allow the boot instruction to scroll onto the screen. Where it stops may give some clue as to what Ubuntu doesn't like in your system. There are several possible causes for what is causing your problem. It may take some detective work and shrewd guesses to figure it out.

---

### Post by Mossey on 2010-10-18
I am not very knowlegdable is this area. On the USB drive I went into boot folder - grub - config file and removed quiet spash the 3 times it was in the line of text using notepad and saved the file. Tried again to run Ubunto from USB drive and nothing was any dfferent. I figured iit should get hung up at some point with some error messages. Nada!

---

### Post by ronparent on 2010-10-19
When the grub menu pops up, move your cursor to the item you want to boot and enter 'e' to edit. move the cursor down to the boot line (the line with 'quiet splash') go to the end of line and backspace to erase them. Then <ctrl>x to boot. You will have to do this each time you want to boot with 'quiet splash' deleted.

---

### Post by Mossey on 2010-10-19
I am a little bit thick in the head! I don't see an opportunity to complete your suggestions. On my desktop computer, after I power up I have maybe 2 secs of scrolling text before what looks like a picture of a USB Drive=Ubunto Guy(Stick figure) pops up then it holds for a few seconds where I have no keyboard control then continues on to loading Ubunto screen that it never leaves. Is there an option to be able to have control, while the above is happening.

---

