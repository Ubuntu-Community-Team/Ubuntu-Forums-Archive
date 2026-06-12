---
title: "Easiest way to create a bootable flash drive installation of Ubuntu"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by jmvizanko on 2012-12-06
So I have a 64Gb flash drive that I would like to turn into a stand alone bootable Ubuntu installation.  I know how to create the flash drive as just the OS, but what is the easiest way to also create separate partition space on the drive for storage of files I use within Ubuntu on the drive?  I have found some guides online, but many are very old, and many involve a lot of hassle.  I also did some searching here, so I apologize if I didn't find a redundant thread.

Also, I know there are inherent risks in keeping it all on one flash drive.  Is it possible to backup the entire image of a flash drive, different partitions and all, in one easy copy?

Thanks for any help.

---

### Post by oldfred on 2012-12-06
Your flash drive is no different than any install to a second drive. Just a bit slower, but functional. But you probably want to make a few settings to reduce writes which helps some on speed.

As I wanted to learn about gpt partitioning I used gpt on my 16GB flash. (You do not have to, most suggest MBR/msdos). I just used gparted and created partitions like any other drive. But you have to use manual install or Something Else to get the option on where to install grub2's boot loader. And you want the boot loader in the MBR of the flash drive. Default installs put boot loader on sda.

Like any install you should be backing up important data. I do not backup system as I will just reinstall but backup my data, /home and some settings from /etc.

If you want compatibility with Windows the first partition must be FAT32 or NTFS as with flash drives Windows only sees first partition.

       HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)


If you want encryption, but LVM will limit compatibility and add some complexity.
       
 Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

    
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by C.S.Cameron on 2012-12-07
Following is step by step for installing 12.04 on a 64GB flash drive on an Intel machine. 12.10 is almost the same.
This is just like doing a normal install to internal drive except for the option of making the first partition FAT32 (or NTFS) so Windows can see it.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue.

At "Installation type" select "Something else".
Continue
Confirm Device is correct.

Select "New Partition Table".
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Make "Size:" about 66000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system".
And Mount point = "/windows".
Select "OK"

Click "free space" and then "Add".
Select "Size:" = 4000 to 6000 megabytes, "Primary", Beginning of this space, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Size ..." = 1000 to 4000 MB, "Primary", Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can update grub later, if you wish.

---

