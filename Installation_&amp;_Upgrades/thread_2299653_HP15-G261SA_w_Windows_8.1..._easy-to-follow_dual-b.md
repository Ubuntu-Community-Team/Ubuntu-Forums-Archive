---
title: "HP15-G261SA w/ Windows 8.1... easy-to-follow dual-boot instructions?"
date: 2015-10-20
forum: Installation &amp; Upgrades
---

### Post by t0p on 2015-10-20
I have a HP15-G261SA w/8.1, and I want to dual-boot Ubuntu.  I have a Ubuntu 14.04.3LTS iso ready to rock and roll.  My problem is finding easy-to-follow dual-boot instructions.  Although I've been using Ubuntu for many years, I have next-to-no Windows know-how, and as soon as instructions start babbling Windows jargon I'm lost (I'm the man who still doesn't understand why you have to go to the "Start" menu to turn the machine off...).  My last Ubuntu installation was on a laptop w/ Windows 7, which was sweet.  But now this UEFI business has got me stumped.

I've defragged Windows 8.1, I have created the Windows 8.1 recovery DVDs... and that's it.  I read I should use the Windows partition tool to create the Linux partitions... but that's all she wrote.  No info on how many partitions I can make, what *kind *of partitions they should be... I'm scared I might screw the machine up, notwithstanding my recovery disks.  I haven't got a lot of money, and I can't afford to kill the laptop.

**HP15-G261SA specs:**
1TB HDD, 4GB RAM, [COLOR=#000000][FONT=Arial]quad-core AMD APU; DVD-RW drive, [/FONT][/COLOR][COLOR=#000000][FONT=Arial]USB 3.0 x 1, USB 2.0 x 2.

[SIZE=2]On a related note:  if I decided to forget the Windows 8.1 on the laptop (I wouldn't use it v much anyway), and if I chose to install Ubuntu 14.04.3 on the entire disk, would that installation be as straightforward as it would be on a computer with BIOs?  Or has UEFI changed everything?

Cheers!
t0p[/SIZE][/FONT][/COLOR]

---

### Post by t0p on 2015-10-21
BUMP!!!!  I wish someone would help me out here.  Maybe even post (a link to) an idiot's guide to dual-booting with UEFI machines....   I usually find Ubuntuforums.org very helpful.  So how do I get Ubuntu onto my HP15-G261SA...?

---

### Post by james_moore2 on 2015-10-21
If you want to dual boot, turn off secure boot and when you install Ubuntu there should be something along these lines "Install alongside Windows 8.1".

---

### Post by yancek on 2015-10-21
Don't use UEFI myself so about all I know is if you have one system UEFI then the other must be also.  The reverse is also true and you can see a lot of posts here from people who installed without doing this.  Also, best to have a 64bit Ubuntu iso.  You can check to see if you already have an EFI partition with your windows install using GParted which is on the Ubuntu medium.  The Ubuntu documentation at the link below and looks pretty detailed.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Dennis N on 2015-10-21
This is a pretty good guide to dual booting windows 8 and ubuntu with uefi:

[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Take a look.

---

### Post by Geoffrey_Arndt on 2015-10-21
+1 for the dedoimedo link.   His articles are excellent.

Re the install - - sometimes removing Windows is NOT a good idea for certain PC models (and HP is one of the problematic ones).   That's because you may need certain boot files from the Windows boot partition (sda1) and the efi directory.

If you do go the single OS route though, you will not only need to disable secure boot (in the efi firmware setup screens), but enable legacy (MS-Dos MBR) mode.   But imho, removing Windows shouldn't be first step you try.

After defrag operation, the Windows main OS partition need to be reduced (shrunk down) using the Windows OS tools.   After the resize, Windows should be restarted to allow chkdsk to run and map the new disk parameters.   Then, do a second reboot to ensure Windows starts normally.   Do not try to create Linux partitions or file systems in Windows.   (the installer will do that via "something else" option in install process).

My summary cheat sheet basically says to do the dual-boot, must have/do:

>   64 bit Ubuntu Install image on DVD or USB-Stick (not SD card),
>   Fast/Quick Start (aka Fast/Quick Boot) needs to be off, including "hibernation" (important),
>   Secure boot needs to be off (can turn it back on later after install),
>   Enable internet or wireless in Ubuntu installer, and enable updates and 3rd party apps to install
>   If having Nvidia or ATI graphics chipsets, be prepared to do some boot options such as "nomodeset" post install

But Dedo's link above does a better and more complete job of laying out the details, . . . good luck!

---

