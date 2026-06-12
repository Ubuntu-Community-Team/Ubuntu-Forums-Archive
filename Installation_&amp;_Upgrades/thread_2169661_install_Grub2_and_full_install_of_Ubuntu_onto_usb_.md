---
title: "install Grub2 and full install of Ubuntu onto usb flashdrive"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by zack4200 on 2013-08-23
Hello, as the title indicates, i would like to make a full install of Ubuntu (most likely gonna use Quantal for now) and Grub2 on a flashdrive. I am using a PNY 16GB flashdrive which I have been using as a persistance LiveDisk, but I wanna try doing a full install on the drive, mostly just to learn how :p 

I have searched around a bit but have found mostly a bunch of dead ends, such as this one which has a section for how to do just this, but it has a dead link to an external source [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Could anyone give me the most straightforward least complicated way to do this? Or even just post a link to where that might be located in case I over looked it. (I am not the best searcher sometimes lol) I currently have a LiveCD and am also running Vista so I can use whichever is easier, which I'm guessing will probably be the LiveCD.

Thank you for any help you might provide :D

---

### Post by Dennis N on 2013-08-23
You will need your current 16gb flashdrive with the live environment (and installer), and another one to install the regular Ubuntu onto.  Or, make another installer on DVD or another USB, and reuse your 16gb flashdrive for the regular Ubuntu.

**Copy of a student activity that does this:**

Note: Does not use UEFI. If you are using that, sorry. 

**Computer Lab Activity:**

**Installation of Lubuntu 13.04 to USB Flash Drive**
**Using Lubuntu 13.04 installer and Lubuntu 13.04 live session**


(If you are installing Xubuntu or Ubuntu, they use the same installer, so the steps here should still be usable. Use the dash to find gparted in Ubuntu).

Before beginning, you need:
1) USB flash drive to be used for the installation. Suggested size 8gb or more.
2) Standard Lubuntu Installer, made either as CD/DVD or USB. 

Steps:

Boot the computer from installer on usb flash drive (or cd/dvd) into live session.
Insert flash drive to be used for installation into USB port of computer.

**Live Session of Lubuntu -**
**a) Prepare the USB flash drive for the installation**

Start gparted partition editor: From Application Menu: System Tools > gparted
In the gparted program window:
In upper right: select the device name of the usb flash drive  (probably /dev/sdb if your installer is a dvd, or /dev/sdc if your installer is another usb)
_Unmount any mounted partitions on the flash drive:_ select the partition, then from the menu, Partition > unmount
Repeat for any other mounted partitions.
_Create a Partition Table on the Flash Drive:_
Menu: Device > create partition table.
Use the default (MS-DOS partition table) &#8211; click on Apply
All space is now shown as unallocated.
_Create a New Primary Partition_
Select (left-click) the unallocated space.
Menu: Partition > new
Leave &#8220;Free Space preceding&#8221; as is.
New size (MiB) = initially shows maximum size; subtract 1000 for each gB of RAM on your computer, and edit the value shown. This will be allocated later for linux swap
Leave &#8220;Free Space following&#8221; as is.
Create as: primary partition
File system: ext4
Label: leave blank for now.
Click add.
_Create the Swap Partition_
Left-click to select the unallocated space.
Menu: partition > new
Leave &#8220;Free Space preceding&#8221; as is.
Size: (leave as is)
Create as: primary partition
File system: linux-swap
Label: leave blank
Click add.
Click the check mark on the tool bar (apply all operations)
In the popup dialog, click on &#8220;Apply&#8221;
Wait while partitions are created, then close the dialog.
Close gparted.
Preparation complete, ready to install.

**b) Installing**
Start the installer from the desktop icon.
Language: Choose your language, then Continue
Preparing to Install Window: Mark &#8220;Install this third party software&#8221;. Do Not Mark &#8220;Download Updates While Installing&#8221; (do this later).
Continue.

Installation type:  Mark &#8220;Something else&#8221; and Continue
Select primary partition you made in part (a) from list of available partitions
Click Change (left side, below list), then in the &#8220;Edit Partition&#8221; popup dialog, make these choices:

Size: leave as is
Use as: select &#8220;ext4 journaling file system&#8221;
Check the &#8220;format the partition&#8221; box.
Mount point: select &#8220;/&#8221;

Click OK

_Grub Boot Loader_
At the bottom of the screen, notice &#8220;Device for bootloader installation&#8221; and select the device designation (like sdb) of the correct flash drive, and NOT a partition (which all end in a number, like sdb1). Do NOT choose your hard disk (usually sda, with partitions sda1, sda2, etc.)

_Click "Install Now"_
The installer will now finish the installation, with some information to be supplied by the user.

--------------------------------------------
[End of Activity Sheet]

[Rechecked by installing onto 8gb USB flash drive. Installer was also on a USB flash drive. All are USB 2.0]

Elapsed Time from "Install Now" to completion, filling in any requested information as quickly as possible: 41 minutes. The install time was considerably lengthened by the read/write and transfer speed of the USB flash drives.

_Boot Up Test: Boots and Runs._

Other Comments:

Grub menu shows any installations on the hard drive as well as the new USB, so you could use this flash drive to boot to an OS on your hard drive. The first option is our new USB installation. If we try this USB to another machine, only the default (first) choice (USB) will boot. Portability is questionable due to hardware differences.

Performance is slowed by the flash drive's limitations. But it works. USB 3.0 would improve this.

---

### Post by oldfred on 2013-08-23
It really is just like any install to a second hard drive or external USB hard drive. You do need to use Manual install or Something else just to get the partition screen and the combo box at the bottom which gives the option on where to install the grub2 boot loader. If flash drive is sdb, you want the grub2 boot loader installed to the drive that is sdb, not internal drive nor any partition. Note last link to .png below.

I used 8GB for my install and another 8GB for data. The 8GB root is not large and if used a lot you would need to houseclean regularly. Mine is more to test or as a backup way to boot. I also put ISO in data partition to use as an installer booted with grub2's loopmount.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

      
 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by zack4200 on 2013-08-25
Just one question, does it matter where on the flashdrive I install Grub as long as it's not in a partition? I'm still kinda confused on that part

Thank you both very much. Between both posts I think I've got enough information to feel comfortable to take the leap and try it out once I know for sure about where to install Grub. I'll just post again if I screw it up and need some more help haha

---

### Post by Quackers on 2013-08-25
You need to install grub to the MBR of the flash drive - just selecting /dev/sdb is enough in the drop-down box at the bottom of the partitioning page of the installer (if that is the designation of the flash drive you are installing to). At the device for bootloader installation section.

---

### Post by ubfan1 on 2013-08-25
You didn't say if your machine was UEFI -- and if you are setting up a stick to boot on such a machine (maybe even secure boot).  If so, I found that the bootloader location should be the USB stick's EFI partition (e.g. /dev/sdb1).  If you just give it the USB device (like /dev/sdb), the installer will ignore it and use the EFI partition from the hard disk.

---

### Post by Dennis N on 2013-08-25
> **zack4200 said:**
> Just one question, does it matter where on the flashdrive I install Grub as long as it's not in a partition? I'm still kinda confused on that part

Thank you both very much. Between both posts I think I've got enough information to feel comfortable to take the leap and try it out once I know for sure about where to install Grub. I'll just post again if I screw it up and need some more help haha

You can only install Grub in the MBR or a partition. No other choices. Not considering UEFI here. I don't have computers available with UEFI, so nothing applies to that. Sorry.

Relevant  Part:

> Grub Boot Loader
At the bottom of the screen, notice &#8220;Device for bootloader installation&#8221; and select the device designation (like sdb) of the correct flash drive, and NOT a partition (which all end in a number, like sdb1). Do NOT choose your hard disk (usually sda, with partitions sda1, sda2, etc.)

You use the partitions only in a multiboot situation, just to put the unwanted Grub somewhere if you already have a grub installation you plan to keep.

---

### Post by zack4200 on 2013-08-26
> **Quackers said:**
> You need to install grub to the MBR of the flash drive - just selecting /dev/sdb is enough in the drop-down box at the bottom of the partitioning page of the installer (if that is the designation of the flash drive you are installing to). At the device for bootloader installation section.

Okay I think I've got it.

Just for my own knowledge, what does MBR mean? I'm pretty much a noob as far as Linux goes, so I have no idea what most of the terms y'all are using mean lmao. 

> **ubfan1 said:**
> You didn't say if your machine was UEFI -- and if you are setting up a stick to boot on such a machine (maybe even secure boot).

I'm not sure that I know what UEFI is, but I know that my laptop does not have it based on what I have read in other posts on the forum.

---

### Post by zack4200 on 2013-08-26
Am I supposed to do anything with the "linux-swap" partition I made?
I don't see anything mentioned about it after creating it. 

Thanks again for all the input


EDIT: I just answered my own question. I selected the partition then clicked "Change..." and saw that it already knew it was gonna be used for swap. I feel accomplished haha.

---

### Post by Quackers on 2013-08-26
Lol.
MBR stands for Master Boot Record.

Is it installed and booting?

---

### Post by zack4200 on 2013-08-28
> **Quackers said:**
> Lol.
MBR stands for Master Boot Record.

Is it installed and booting?

Okay, I guess that's good to know. 

And yup, its working perfectly. I had a little bit of trouble getting the wireless drivers to work on this laptop but it wasn't too frustrating as I've had Ubuntu on it previously so I was expecting it and knew mostly how to get it figure out, so between that and various posts about the Broadcom wireless drivers I've gotten that taken care of. I haven't had a chance to try booting on any other computers yet, but I'll update this post with whether or not it works lol. 

One last question, at least for now. How do I change the thread to say solved? I've never done it from my phone before

---

### Post by Dennis N on 2013-08-28
Look here:

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

