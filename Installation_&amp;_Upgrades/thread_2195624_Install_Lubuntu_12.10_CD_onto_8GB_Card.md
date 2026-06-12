---
title: "Install Lubuntu 12.10 CD onto 8GB Card"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by jefgungil on 2013-12-25
Rather than grubbing up my c: drive, I want install Lubuntu on a separate 8GB memory card. Two questions:

1. I can't find instructions on how to do that, so I'm asking y'all.

2. Once that's done, I'm assuming that if that card is inserted when I reboot the PC, it'll boot into Lubuntu and if the card is out, it'll boot into Windows as usual... true?

---

### Post by jefgungil on 2013-12-26
Same question would also apply to installing on a USB flash drive.

---

### Post by efflandt on 2013-12-26
It depends what type of device the memory card is in. Memory card slots in desktops (and my Acer W500P tablet) are internally USB connected and as usb mass storage (like external USB sticks/card readers) can be installed to like a hard drive and boot fine, depending upon BIOS boot order or hot key during boot. However, card slots in laptops are often a different type of mmc(?) block device which cannot be booted from.

Basically a regular install to USB memory or drive involves selecting "Other" during the partitioning install phase (not entire hard drive or side by side), make sure that you have the proper device, set up Linux partition(s) on it, and either in that step (at bottom of screen) or following step, install grub to the mbr of that device, instead of default to hard drive. In some cases (like Dell) even if you set BIOS to boot USB before hard drive, if previous boot was not from that USB you might still need to press a hot key during BIOS splash to select boot device. That is probably a safety feature so you do not accidentally boot something potentially malicious from CD/DVD or USB (the only virus I ever caught was a boot sector virus from a floppy disk).

---

### Post by jefgungil on 2013-12-26
Thanks... it's an old HP desktop, cutting edge in '05, with 4 card slots and only four USB jacks. Turns out that my 8GB card is completely dead, so I'm going to get a new one tomorrow &#8211; do I want a card or a stick?

---

### Post by C.S.Cameron on 2013-12-26
Some computers of your vintage do not boot cards, most should boot sticks.
The best USB2 device I have found is the SanDisk Cruzer Fit.
There are two popular methods of installing to USB, Persistent install and Full install.

Persistent install 12.04, 12.10 is similar:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.


Full Install 12.04

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
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
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)

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
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

### Post by jefgungil on 2013-12-27
Wow. Thank you very much for going through all that trouble. But I have a feeling you wasted your time doing it &#8211; way over my head. I just figured I'd click this, then click that, and voila. I may try it, but it'll be pushing my curiosity to painful levels... thanks again. Hopefully someone here can make use of your work.

(Last year, I did partition my c: and install Lubuntu and its grub. Undoing that was pushing my limits too.)

---

### Post by C.S.Cameron on 2013-12-27
No problem, the stuff was already written as the same question gets asked many times.

It is really not that complicated, I just wrote down every step.

Doing a Full install to USB is just about the same as installing to internal hard disk.

Making a Persistent USB using UNetbootin or Startup Disk Creator takes just a few button clicks.

Most of the above is just frill.

---

### Post by jefgungil on 2013-12-27
> if after partitioning you choose to install grub to the root of the usb drive 

I was hoping, by installing Lubuntu on a seperate, removable drive, to not have to install grub at all. If the drive was in, the PC boots Lubu, if not, Win7. Just mentioning in case I attempt your instructions, of course.

---

### Post by jefgungil on 2013-12-28
No idea why I didn't find this earlier, but I also may try [URL="http://ubuntuforums.org/showthread.php?t=1872303"]HOW TO Install Lubuntu on USB Drive
[/URL]

---

### Post by 0N3 on 2013-12-28
I managed to get Ubuntu installed on the 16 GB microSD card on my Galaxy SIII, boot any computer with it plugged in via USB. I did it via the persistent Install using a tool called Lili USB Creator

---

