---
title: "Installation nightmare"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by Destination on 2011-11-26
I am attempting to load 10.04 on an Acer Aspire One A110 netbook. This computer has an 8GB solid state drive which should be far more than adequate for the system software.

Earlier, I had been using an older version of Ubuntu on the netbook, but because of a corruption, I have had to do a reinstall.

To acquire the files, I have used Unetbootin to put the data onto a USB thumbdirve. I am using a Mac to do this.

When I connect the USB drive to the netbook and set it to boot from that drive, the computer gives me a message that there is no system installed.

To troubleshoot, I have used three different thumbdrives and I have tried several versions of Ubuntu.  All drives are formatted as FAT32.

Is this an issue with a bad computer or is there something I am missing or neglecting? 

Your help is appreciated.

Thanks.

---

### Post by fantab on 2011-11-26
> **Destination said:**
> I am attempting to load 10.04 on an Acer Aspire One A110 netbook. This computer has an 8GB solid state drive which should be far more than adequate for the system software.

Earlier, I had been using an older version of Ubuntu on the netbook, but because of a corruption, I have had to do a reinstall.

To acquire the files, I have used Unetbootin to put the data onto a USB thumbdirve. I am using a Mac to do this.

When I connect the USB drive to the netbook and set it to boot from that drive, the computer gives me a message that there is no system installed.

To troubleshoot, I have used three different thumbdrives and I have tried several versions of Ubuntu.  All drives are formatted as FAT32.

Is this an issue with a bad computer or is there something I am missing or neglecting? 

Your help is appreciated.

Thanks.

Tell your BIOS to boot from USB first. If you have already done that then check to see that you are burning .ISO to the Disk properly, at the slowest possible speed (if you are using MAC then have you converted the .iso to .img?) and that you have created a working Startup Disk.

The following is the copy/Paste from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
The instructions are to create Ubuntu USB using MAC.

> [SIZE=1][COLOR=DarkGreen]We would encourage Mac users to download Ubuntu Desktop Edition by  burning a CD for the time being.[/COLOR] But if you would prefer to use a USB,  please follow the instructions below.[/SIZE]
             
             [SIZE=1]Note: this procedure requires an .img file that you will be required to create from the .iso file you download.[/SIZE]
             
             [SIZE=1]TIP: *Drag and Drop* a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.[/SIZE]
             
             
[LIST=1]
[*][SIZE=1]Download the desired file[/SIZE]
[*][SIZE=1]Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)[/SIZE]
[*][SIZE=1]Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)[/SIZE]
[*]                     [SIZE=1]**Note:** OS X tends to put the .dmg ending on the output file automatically.[/SIZE]
[*][SIZE=1]Run diskutil list to get the current list of devices[/SIZE]
[*][SIZE=1]Insert your flash media[/SIZE]
[*][SIZE=1]Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)[/SIZE]
[*][SIZE=1]Run diskutil unmountDisk /dev/diskN (replace *N* with the disk number from the last command; in the previous example, *N* would be 2)[/SIZE]
[*][SIZE=1]Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).[/SIZE]
[*]
[LIST]
[*][SIZE=1]Using /dev/rdisk instead of /dev/disk may be faster.[/SIZE]
[*][SIZE=1]If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.[/SIZE]
[*][SIZE=1]If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.[/SIZE]
[/LIST]
 
[*][SIZE=1]Run diskutil eject /dev/diskN and remove your flash media when the command completes[/SIZE]
[*][SIZE=1]Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick[/SIZE]
[/LIST]
         


---

### Post by Destination on 2011-11-26
I tried that but when I load the drive on the netbook, I still get the message there is no system or I get L 99 99 ... I've been trying with the Live version of the system software. Should I be using something different?

---

### Post by fantab on 2011-11-26
> **Destination said:**
> I tried that but when I load the drive on the netbook, I still get the message there is no system or I get L 99 99 ... I've been trying with the Live version of the system software. Should I be using something different?

Exactly how much Memory does your net-book has?  and How much HDD space do you have? Are you dual-booting? Do you by any chance have LILO boot loader on your netbook?

**[Read This: For Installation from USB Disk.]("https://help.ubuntu.com/community/Installation/FromUSBStick")**

[**Read This: especially the sub-topic, *comments and troubleshooting***]("https://help.ubuntu.com/community/USB%20Installation%20Media")

I suggest, if you can, try and burn the .ISO to the USB Disk using Windows or any other Distro.

---

### Post by Destination on 2011-11-27
I've made progress, although it seems there should be an easier method than the workaround I've used.

My method worked as follows:

1. Burn a Live download of Ubuntu onto a CD. This is a simple process on a Mac. Instructions are on Ubuntu.com. 

2. Boot the Mac from the Ubuntu CD. (To force the computer to boot from the CD, press C on the keyboard at startup.) The Ubuntu CD does not like the wireless keyboard and mouse. Use a wired keyboard and mouse instead. At the very least, a wired mouse is required.

3. Use the Startup USB tool in Ubuntu to create a USB that will boot on any machine.

4. This USB will boot the netbook — any computer with a USB port — and can install the software.

---

### Post by fantab on 2011-11-27
> **Destination said:**
> I've made progress, although it seems there should be an easier method than the workaround I've used.

My method worked as follows:

1. Burn a Live download of Ubuntu onto a CD. This is a simple process on a Mac. Instructions are on Ubuntu.com. 

2. Boot the Mac from the Ubuntu CD. (To force the computer to boot from the CD, press C on the keyboard at startup.) The Ubuntu CD does not like the wireless keyboard and mouse. Use a wired keyboard and mouse instead. At the very least, a wired mouse is required.

3. Use the Startup USB tool in Ubuntu to create a USB that will boot on any machine.

4. This USB will boot the netbook — any computer with a USB port — and can install the software.

I am glad you've made progress... and a pat on the back for the workaround.

I myself use a wireless Keyboard and Mouse and they both work out of the box with Linux LiveCD.... I think I have Chicony Wireless driver (Open Source).

---

