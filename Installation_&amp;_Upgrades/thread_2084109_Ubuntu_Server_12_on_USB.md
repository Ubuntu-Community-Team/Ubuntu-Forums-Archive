---
title: "Ubuntu Server 12 on USB"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by jumpycore on 2012-11-14
Hi, I've tried googling how to install to a USB stick but haven't come up with what I'm looking for.

I started to install the CD with my laptop (my server has no CD drive) and suddenly realized it wasn't asking for which drive to install to. I'm running 3 3TB drives with ZFS already so I can't install to the drives (i'm switching from FreeNAS which has been giving me major issues).

SO simply, I'm wondering how do I install Ubuntu Server TO a Flash Drive (I have a HAMAS USB 3.0 8GB stick). So far on google all i can find is how to install FROM USB.

Thank you!

---

### Post by C.S.Cameron on 2012-11-14
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine, Installing Server should be similar.

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
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
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
You can revise grub later, if you wish.

---

### Post by oldfred on 2012-11-15
I often refer users to C.S.Cameron's instructions. They really are just like any install to a second drive. You need to use Something Else so you get the option on where to install the grub2 boot loader or else it likes to default to sda.

I think the instructions C.S.Cameron posted were more for a desktop install. The first FAT partition is so you could copy data from a Windows machine. The only other reason for a FAT partition first would be if booting from UEFI, not BIOS.

I used gpt partitioning just to see if I could and it worked without any issue, other than needing the bios_grub partition. gpt has a backup partition table which may offer some advantages otherwise it does not really matter.

```
fred@fred-Precise:~$ sudo parted /dev/sde unit s print
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sde: 31375360s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system  Name          Flags
 1      2048s      4095s      2048s                   KingstonData  bios_grub
 2      4096s      14749695s  14745600s  ext4
 3      14749696s  29327359s  14577664s  ext4
 4      29327360s  31373311s  2045952s   ntfs

```This is the alternative installer which is similar to the server install. He also adds LVM for full encryption which you probably do not need.

Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

While flash is a lot slower than SSD, it still needs some of the same settings to reduce writes.
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode.
change to noop i/o scheduler

---

### Post by C.S.Cameron on 2012-11-15
OldFred is right, you don't need A FAT, (or NTFS), partition for a server, probably don't need a separate home partition either.

---

