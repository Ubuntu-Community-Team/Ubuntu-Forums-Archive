---
title: "ns2 on ubuntu 10.10 in USB"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by sonaliagr on 2011-01-26
Hello,
   I have a bootable USB drive having Ubuntu 10.10 in it. I am able to boot my Windows XP laptop through this USB and Ubuntu desktop appears. It shows two icons on the desktop - Examples and Install Ubuntu10.10. I think it is booting into the live session. I want to install NS2 software on Ubuntu 10.10 in this USB itself. I dont want to install the software on the laptop's hard disk. 
Yesterday, i made a directory in home which is not there when i booted into Ubuntu again today. While trying to install NS2, it shows a number of errors. Could you please help me out with this. How should i proceed further to have both Ubuntu 10.10 and NS2 V2.34 in my external USB drive. 

Thanks

---

### Post by oldfred on 2011-01-26
How big is your flash drive. If 4GB or less all you can do is add persistence. If 8GB or more you can do a full install that lets you do anything that a normal install does. Just that flash is slower than a hard drive and USB is slower than a hard drive, but speeds are still usable.

Benefits of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by C.S.Cameron on 2011-01-26
Have you seen the following about installing NS2 in Ubuntu?

[http://getch.wordpress.com/2010/10/25/installing-network-simulator-in-ubuntu10-10/](http://getch.wordpress.com/2010/10/25/installing-network-simulator-in-ubuntu10-10/)

You should be able to install this in a persistent install.
Use the Startup Disk Creator on the Live USB and select enough extra space to suit.

You could also do a Full install as OldFred mentions above, It will fit onto a 4GB flash drive, if you don't need to add a lot of extras.

---

### Post by sonaliagr on 2011-01-27
> **oldfred said:**
> How big is your flash drive. If 4GB or less all you can do is add persistence. If 8GB or more you can do a full install that lets you do anything that a normal install does. Just that flash is slower than a hard drive and USB is slower than a hard drive, but speeds are still usable.

Benefits of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
I am having a 4GB pen drive and am able to see the live session of Ubuntu 10.10 Desktop Edition. HOw should i run "gksu nauilus"? And is it possible to do full install using the link you have mentioned in the same USB.

---

### Post by sonaliagr on 2011-01-27
> **C.S.Cameron said:**
> Have you seen the following about installing NS2 in Ubuntu?

[http://getch.wordpress.com/2010/10/25/installing-network-simulator-in-ubuntu10-10/](http://getch.wordpress.com/2010/10/25/installing-network-simulator-in-ubuntu10-10/)

You should be able to install this in a persistent install.
Use the Startup Disk Creator on the Live USB and select enough extra space to suit.

You could also do a Full install as OldFred mentions above, It will fit onto a 4GB flash drive, if you don't need to add a lot of extras.
Hello,
  I am following the same link which you have mentioned. I followed the steps till Try It. Then while installing, i did not do it since i wanted to get it installed in my USB itself and not on my laptop's hard disk. I am having a 4GB pen drive.

---

### Post by C.S.Cameron on 2011-01-27
> **sonaliagr said:**
> I am having a 4GB pen drive and am able to see the live session of Ubuntu 10.10 Desktop Edition. HOw should i run "gksu nauilus"? And is it possible to do full install using the link you have mentioned in the same USB.

You can press F2 and then gksu nautilus or run it from terminal.
4GB is big enough if you do not plan on adding a bunch of other stuff.

Full Install 4GB drive:

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
Select "Primary", "New partition size ..." = 3 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (~1 GB), Beginning and "Use as" = "swap area" then OK.
**(Important)**
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

### Post by sonaliagr on 2011-01-27
> **C.S.Cameron said:**
> You can press F2 and then gksu nautilus or run it from terminal.
4GB is big enough if you do not plan on adding a bunch of other stuff.

Full Install 4GB drive:

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
Select "Primary", "New partition size ..." = 3 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (~1 GB), Beginning and "Use as" = "swap area" then OK.
**(Important)**
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
Thanks for the reply. I understood the process but i do not have Ubuntu CD with me. I have the ISO image from which i have created the Live USB for Ubuntu10.10 desktop edition. In that case, if i plug in my USB and use the prompt "Install" and then select  At "Allocate drive space" select "Specify partitions manually  (advanced)" , will it work. Will i get the full installation on my 4 GB pen drive?

---

### Post by oldfred on 2011-01-27
You need  a liveCD, a second USB, or modify grub to loopmount the ISO directly from the hard drive to allow you to install to the flash drive.

With the 4GB flash drive the install is over 3GB, so you will have to regularly houseclean and not add a lot of other software.

Hard drive:
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by C.S.Cameron on 2011-01-27
> **sonaliagr said:**
> Thanks for the reply. I understood the process but i do not have Ubuntu CD with me. I have the ISO image from which i have created the Live USB for Ubuntu10.10 desktop edition. In that case, if i plug in my USB and use the prompt "Install" and then select  At "Allocate drive space" select "Specify partitions manually  (advanced)" , will it work. Will i get the full installation on my 4 GB pen drive?

Yes, you can install to USB from a Live USB.
Make sure the boot loader is put on the right drive.
As OldFred says a 4GB flash drive is tight but will work.

---

