---
title: "can't switch from ubuntu to dual boot (xp and ubuntu)"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by goustaroubunta on 2010-11-13
i have my gf's acer aspire one and it is very urgent to put xp in that because her studies demand so.

i have installed ubuntu netbook remix 10.10 using all the disk.

and now i cant install windows because they don't recognize the ext4 format...

i've tried various stuff.... is there any solution to this?

---

### Post by searchfgold6789 on 2010-11-13
[CENTER]-----  METHOD 1  -----
[/CENTER]

You must first shrink the Ubuntu partitions. This can be done with a [_**gparted live cd**_]("http://partedmagic.com/").

Then, you must install windows XP on the space you left over after you shrunk Ubuntu.

Then, you must go back into the Live CD and open up a terminal. At the prompt type in ```
sudo grub-install /dev/sda
```Once it finishes, type ```
sudo update-grub
```[RIGHT][CENTER]-----  METHOD 2  -----
[/CENTER]
[LEFT]
Remove Linux with the Ubuntu Live CD.

Then install XP using about a third of the hard disk space.

Then install Ubuntu on the other unused space.

[RIGHT][CENTER]-----  METHOD 3 -----
[/CENTER]
 
[LEFT]There is a program for Ubuntu called Wine. It allows you to install and run Windows programs. You can get the program from the Ubuntu software center and it will allow you to run all your favorite Windows programs such as Office or World of Warcraft.
[/LEFT]
[/RIGHT]
[/LEFT]
[/RIGHT]

---

### Post by Dr. C on 2010-11-13
Have you considered using Virtualbox to install XP in a virtual machine? The OSE edition of Virtualbox is available from the Ubuntu software centre. Here is some information on Virtual Machines and Virtualbox [https://help.ubuntu.com/community/VirtualBox]("https://help.ubuntu.com/community/VirtualBox").

The other option is to set up a dual boot system [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by goustaroubunta on 2010-11-14
thanks Search and C.. i created a FAT partition with a live usb and used the multiboot program but still $%#^&. it says hal.dll file is corrupt. also the hard drive is not detected. the c: disk is the usb i've plugged in to do the job! and no other partition is there in the xp setup.


how do i "Remove Linux with the Ubuntu Live CD"??

those sound easy but are terrible to really do in a short period of time..

---

