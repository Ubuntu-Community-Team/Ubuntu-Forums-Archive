---
title: "Unetbootin frugal install - of latest Ubuntu - issue"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by thepowerofnow on 2017-02-11
[LIST]
[*]I attempted to frugal install the latest Ubuntu via Unetbootin. 
[*]I partitioned the hard-drive - which previously contained only Windows 7 Professional - giving it a 100GB section for Ubuntu. 
[*]I recall leaving the partition in a raw state as I read that Ubuntu would recognize and deal with this on its own. 
[*]I booted into Ubuntu 'try before install' version via Unetbootin. 
[*]I proceeded to initiate the install procedure. 
[*]At the beginning of the install I was presented with a partition screen. 
[*]I recall selecting ext4 as the filesystem and / as the 'boot' point for the 100GB partition. 
[*]The install appeared to be successful and I was prompted to reboot. 
[*]I rebooted my computer but I was only presented with Windows 7 and Unetbootin at the boot screen. 
[*]When I booted back into Unetbootin there appeared a hard-drive icon on the bottom left of the screen - as part of the icon bar containing other Ubuntu applications. I clicked the icon and I saw about 20 folders and a couple of files. They appear to be the files of the install I had just attempted. I think the icon indicated a size of 105GB - not sure why. I'm sure I only allocated for 100GB. 
[/LIST]

So that is the current situation. I don't have access to CD or memory stick so frugal install is my only option. I would appreciate some help with this. Thanks

---

### Post by Bucky Ball on 2017-02-11
Welcome. At the end of the install, when you are asked to restart the computer, you are also asked to remove the install media, which it doesn't sound like you did.

Switch off the machine, take out the USB, boot up and get into your BIOS and make sure you have the boot priority set to the hard drive, continue and let us know what happens.

When you say a 'frugal install', what exactly do you mean? Did you use [the Ubuntu minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") or you downloaded the ISO image to a hard drive and installed from there? More details, please. Also, if that latter, where does UNetbootin come into this?

---

### Post by yancek on 2017-02-11
It doesn't seem as if you understood what a frugal install is.  There was no need to create a separate partition for the Ubuntu as it is installed to your hard drive and is the same as a Live CD/DVD or flash drive except that it is on the hard drive.  It is a read-only system and any changes you make to it will be lost on reboot.

> I rebooted my computer but I was only presented with Windows 7 and Unetbootin at the boot screen.

That is expected behavior with a frugal install.  Frugal install with unetbootin explained at the link below in the section "Hard Disk Install Mode".

[https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

---

### Post by thepowerofnow on 2017-02-11
I will try to clarify based on the answers so far:


[LIST]
[*]I did not use a USB. I am attempting to install without USB or CD. This was my understanding of what is meant by 'frugal install'. I wasn't prompted to remove media as I didn't use USB or CD.
[*]I installed Unetbootin from inside windows 7. I downloaded Ubuntu ISO and selected that file for the diskimage. I selected hard-drive for device type:
[*][IMG]https://unetbootin.github.io/screenshot2.jpg[/IMG]
[*]I Ok'd and UNetbootin done its thing.
[*]I then rebooted and selected the new UNetbootin option.
[*]I was booted into Ubuntu try version.
[*]I proceeded to install Ubuntu from here. That is where my previous thread begins.
[/LIST]

I can sort of intuit that I have made a noob mistake here. But I do hope someone can help me because I really want Ubuntu asap.

---

### Post by Bucky Ball on 2017-02-11
In that case, I know nothing about frugal installs, but I do know you have UNetbootin setup to install to the USB drive you have plugged which Windows is seeing as D:\. Is that correct? Would have thought that should be pointing to a partition ... :-k

---

### Post by thepowerofnow on 2017-02-12
Sorry Bucky. That was just a picture I picked up from the web to show you what I was using. I didn't configure it like it shows in the picture.

---

### Post by yancek on 2017-02-12
Better to just shrink the windows partition and leave the space unallocated as you will need to format the partition with a Linux filesystem during the install anyway.  Default windows systems are not able to do this.  Since you ran the Ubuntu installer from the 'frugal' unetbootin, and selected the partition you had created earlier and the mount point '/' and ext4 filesystem which should all be correct, the question then is what option did you select for Device for bootloader installation.  Drives in Linux have names such as sda, sdb, etc and the default is to install to /dev/sda and obviously that wasn't done or if it was selected, it failed.

Did you use the manual option during the install which is referred to as 'Something Else'?
Do you want the Ubuntu Grub bootloader to boot both Ubuntu and windows?   The simplest way to do that is to select '/dev/sda' during the install if sda is the correct drive.  It is possible to boot a Linux system from the windows bootloader but it is a multi-step process and not as simple as installing/using Grub.

You might post the output of the command:  sudo fdisk -l(lower case Letter L in the command) by booting from the frugal unetbootin option on your boot menu.
You may be able to simply install Grub to the MBR to resolve the problem.

---

### Post by thepowerofnow on 2017-02-16
[LIST]
[*]I acquired a USB stick.
[*]I went through the process of saving .iso of Ubuntu and made it ready for install etc.
[*]I told Ubuntu install to overwrite anything on the disk and make Ubuntu the sole operating system.
[*]Ubuntu install proceeded until it failed stating there wasn't enough space on the partition.
[*]I booted back into Unetbootin Ubuntu try version and wiped the partition I had created for Ubuntu previously.
[*]I then attempted to re-boot via USB as a second attempt at Ubuntu install.
[*]Now I get nothing but a flashing underscore at the top left of my screen.
[*]USB is set as first priority for boot.
[/LIST]

When I boot without USB I get:

Initializing and establishing link.....

Media test failure check cable. 
Exiting Intel boot agent. 

It then goes to boot menu and shows my ATA HDD0 hard drive and PCI LAN in that order.

I have just re-saved Ubuntu - via Rufus(I used Rufus previously too) - onto the USB. 
Whilst my computer was on boot menu I inserted USB. Ubuntu now seems to be loading so I will again attempt an install and hope it over-writes everything as I asked it to previously.

---

### Post by thepowerofnow on 2017-02-16
The issue has been solved. I now have a successfully installed Ubuntu OS. 
I wiped the drive with Gparted from a live USB iso and proceeded with a successful install.

---

### Post by C.S.Cameron on 2017-02-16
Thank you for the update, please mark the thread as solved.

---

