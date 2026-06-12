---
title: "Dual boot woes."
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Ghost Pirate on 2008-04-11
I have been using Ubuntu on an old P4 system for almost a year now, and I love it.  I decided to install it on my main system (Intel Core 2 Quad Q6600, 4GB DDR2 RAM, GeForce 8800GT, 320GB SATA HDD with WinXP, 160GB HDD empty) for video editing (Cinelerra).  Since I had the extra 160GB HDD, I decided that would be the destination for Ubuntu.  I disconnected the primary HDD, moved the other HDD to the SATA1 port, booted the system from the LiveCD and installed.  I connected my Windows HDD to the SATA2 port, turned on the computer, selected Ubuntu from GRUB, logged in, and edited the menu list for GRUB to give the option to boot WinXP (I have seen how to do this many times in these forums).  After reboot, I selected WinXP from GRUB, and get an error that C:\windows\system32\ntoskrnl.exe is corrupt and windows can not start.  I booted the system with the XP disc, went into the recovery console, and ran this command: 
copy h:\i386\driver.cab c:\system32\ntoskrnl.exe
rebooted, still had the same issue.  Fixed the MBR (even though this drive was not connected during install of Ubuntu) and that didn't help.  When I disconnect the Linux HDD, and move the Windows HDD to SATA1, Windows boots just fine.  I just can't seem to get Windows and GRUB to play nice together.  I saw a post from somebody somewhere about loading GRUB into the Windows Bootloader.  Would this be my best option at this point?  I would like to use Ubuntu on that system, but not at the expense of Windows.  My wife is a graphics designer, and Adobe doesn't play well with Linux (Gimp is good for me, but it's not Photoshop; and there is NO open source alternative to InDesign or Bridge).

---

### Post by Tatty on 2008-04-11
You need to use the super grub disk to rewrite grub to your comp.  I cant give you any more details on this as i have never had to do this before myself. [http://forjamari.linex.org/projects/supergrub/]("http://forjamari.linex.org/projects/supergrub/")

Alternatively you could restore grub using the ubuntu live cd... [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Ghost Pirate on 2008-04-11
I've used Super Grub.  The system boots just fine when just one HDD is installed, and boots into Ubuntu when both are installed.  However, I can't get it to boot into Windows with both HDDs connected.

---

### Post by bartos on 2008-04-11
You might want to try leaving the windows drive on sata1 as windows need to think it is "C" drive and if it thinks it's "D" it won't start because none of the files point to a "D".

Leave windows where it boots and reinstall ubuntu. Grub will pick it up properly and all should be well.

Good Luck

---

### Post by Ghost Pirate on 2008-04-11
I was going to try that, but I was under the impression that doing that would cause GRUB to be installed in the MBR for the HDD in SATA1, regardless of whether that drive is where you're installing Ubuntu or not.  If that is the case, I still won't be able to boot into Windows without fixing the MBR; but fixing the MBR gets rid of GRUB.

---

### Post by bartos on 2008-04-11
Yes Grub will be installed to the mbr of the windows drive but grub will point to ntloader to boot windows for you when you choose the optoin on grub menu.

It will be fine.

---

### Post by Ghost Pirate on 2008-04-11
Moved the Windows HDD back to SATA1, booted Super Grub to put grub on that drive.  Still getting the same error.  Ubuntu boots just fine, but Windows will not.  I think I'll try loading grub into the windows boot loader, see if that works.

---

### Post by adrian15 on 2008-04-11
> **Ghost Pirate said:**
> I disconnected the primary HDD, moved the other HDD to the SATA1 port, booted the system from the LiveCD and installed.  I connected my Windows HDD to the SATA2 port, turned on the computer, selected Ubuntu from GRUB, logged in, and edited the menu list for GRUB to give the option to boot WinXP (I have seen how to do this many times in these forums).  After reboot, I selected WinXP from GRUB, and get an error that C:\windows\system32\ntoskrnl.exe is corrupt and windows can not start.  I booted the system with the XP disc, went into the recovery console, and ran this command: 
copy h:\i386\driver.cab c:\system32\ntoskrnl.exe
rebooted, still had the same issue.  Fixed the MBR (even though this drive was not connected during install of Ubuntu) and that didn't help.

In my opinion you should follow the *Grub Solution* instructions on [how to boot Windows from a second hard disk](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_From_A_Second_Hard_Disk) and then set Linux hard disk to be the first one to boot in your BIOS.

Then you will be able to boot Windows from Grub with both Hard Disk plugged.

adrian15

---

### Post by David Robertson on 2008-04-11
I have this working. Ubuntu on first drive XP on the second. Pull out the first drive just get XP . It took a while to work out how to do it.

The link supplied above lists the changes to make to the menu.lst. In particular:

map (hd0) (hd1)
map (hd1) (hd0)

These hide ubuntu from XP. Then XP should boot. XP gets confused if it finds another drive/partition in front of it. XP  counts out the partitions and expects to be on the exact same number as installed. It uses  the wrong drive/partition and goes BANG! No damage done; just won't boot.

The style (eg hd0) should match your menu.lst. There another file in grub that maps these names to what ubuntu calls the drives. As long as you follow your given style, Ubuntu should follow your lead.

Once you finally boot XP and access the disk manager, the Ubuntu partition will be marked 'hidden'.

I think it's a better method than booting ubuntu from XP, mainly because it leaves your XP drive completely untouched.

---

### Post by adrian15 on 2008-04-11
> **David Robertson said:**
> 
The link supplied above lists the changes to make to the menu.lst. In particular:

map (hd0) (hd1)
map (hd1) (hd0)


There is also a change in ```
rootnoverify (hd0,0)
``` which becomes: ```
rootnoverify (hd1,0)
```.

adrian15

---

### Post by Ghost Pirate on 2008-04-11
Okay, I removed the drive with Ubuntu installed, and Windows booted normally.  I moved the Windows HDD to SATA2, put the other HDD on SATA1, booted from the live CD and started over with a clean install of Ubuntu.  Followed all of the suggested steps, and I'm still getting the ntoskrnl.exe corrupt error.

---

### Post by adrian15 on 2008-04-12
> **Ghost Pirate said:**
> Okay, I removed the drive with Ubuntu installed, and Windows booted normally.  I moved the Windows HDD to SATA2, put the other HDD on SATA1, booted from the live CD and started over with a clean install of Ubuntu.  Followed all of the suggested steps, and I'm still getting the ntoskrnl.exe corrupt error.

I do not believe that you have followed all the steps. But it doesn't matter. Please tell us if using a [Super Grub Disk](http://www.supergrubdisk.org) ** Super Grub Disk (With Help) -> Windows -> Boot Windows from 2nd Hard Disk** boot your Windows.

If it does not work you might have a partition recovery partition somewhere. Can you please tell us what you see in Super Grub Disk when going to: Super Grub Disk (with Help) -> Boot & Tools -> Show Partitions[/b] and selecting hd0.? And when selecting hd1?

Note: Just select  a partition to come to previous menu.

adrian15

---

