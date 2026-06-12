---
title: "Howto: Create your own LiveUSB graphically"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by smartboyathome on 2007-12-22
[CENTER][SIZE="5"]DISCLAIMOR: I am **not** reliable for any damage this may cause.[/SIZE][/CENTER]

Well, there is a way to make a LiveUSB by booting up to an Ubuntu CD mentioned [here]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"), but this tries to make it easier for the new user by using an existing Ubuntu installation and making it graphical. **BEFORE DOING THIS GUIDE, BACKUP ALL DATA ON YOUR USB DRIVE, AS IT _WILL_ BE ERASED.** You must do this with a 1GB or larger usb drive (2gb or larger is recommended for persistance).

*NOTE: This guide focuses on using Ubuntu on your USB drive, but in theory any ubuntu-based distro should work with this. Also, one small portion of this guide has to use the command line. I hope to get rid of this need in the future.*

**_Step One: Install dependancies_**
First, you will need a program called GParted, which is a powerful program that allows you to quickly and easily partition your disks. You can get from [here]("http://www.getdeb.net/search.php?search_distro_id=5&keywords=gparted"). Click the download link, and select open with GDebi Package Installer. Once GDebi opens, install it. You now have GParted installed and can continue with this howto. If you are running Ubuntu 7.10 Gutsy Gibbon, then you don't need to do this, as GParted 0.3.3 is included in the repositories. You can install it by running:
```
sudo apt-get install gparted
```
in a terminal, or by opening up Synaptic and searching for gparted.

**_Step Two: Partitioning the drive_**
Before insterting your USB drive, go to System > Preferences > Removable Drives and Media and uncheck the checkboxes next to "Automount drives when hotplugged" and "Automount drives when insterted". This will make it so that the drives you insert aren't mounted automatically. This is important because otherwise GParted wouldn't be able to partition your disks. You can change these settings back later by doing the opposite if you want.

Now, open up GParted (it should be located in System > Administration), and you should see a dropdown box in the top  right hand corner which says something like "/dev/sda". Change that to the disk which has your USB drive (for me it is /dev/sdc, but it will vary depending on your setup). Once that is up, right click on the partition on your drive and format it to fat32. Now click apply. It will take a few moments, depending on how large your USB drive is. After this completes, right click on it and click manage flags. Check the checkbox next to boot.  It is a good idea to leave these two windows open if you want to have persistance.

Go to Places > Computer and find which disk is the one that you just formatted (it should be called something similar to sdc1, refer to GParted to find out which drive it is on). Right click on it, and select "Rename". Name it ubuntu710.

**_Step Three: Downloading and extracting the LiveCD ISO_**
Now, you will need to download an Ubuntu LiveCD ISO. You can get it from [here]("http://www.ubuntu.com"). If you already have it, then no need to do the former.

Now, after it downloads, open up your file browser and navigate to where you downloaded it. Double click on the ISO to open it in the Archive manager. Extract it to where your USB drive is mounted (mount it by clicking on the drive to the left of the folder in your file browser).

Once this is done, open a terminal to where your USB drive is mounted by typing cd /media/ubuntu710. After this completes, type this in a terminal, substituting x with the partition's name (ie, I did sdc1):
```
syslinux -sf /dev/sdx1
```

**_Step Four: Partitioning drive for persistence_**
To get persistance for Ubuntu, go back to GParted. Resize the partition you formatted earlier to 750MBs for the Ubuntu livecd (the size for this may change depending on the size of the livecd/dvd iso). Format the space created by this to ext2 by right clicking on the gray unformatted space and selecting Format > ext2. Now, push apply. Once it is done, open the window titled "Computer" again (if it isn't open, open it again by going to Places > Computer). Right click on your newly created partition and select "Rename". Rename this paritition to casper-rw.

**_Step Five: Enabling Persistance_**
To enable persistance, you will have to download [this archive]("http://smartboy.salocinlinux.org/db/U710fix.zip") and extract it to your USB drive. To do this, click the link to the archive, and select "Open" in the box that comes up. Once the archive is opened, click "Extract" and extract it to your newly named "casper-rw" partition. If you are asked if you want to overwrite a file, select yes.

**_Step Six: Enjoy your new LiveUSB_**
That is right, you are done! Reboot your computer, set your BIOS to boot to LiveUSB if need be, and enjoy your new LiveUSB drive!

**_FAQ:_**
**GParted crashes on me when I mount or unmount a drive. :(**
This is a bug in Ubuntu's version of GParted.
**Can (insert file manager here) replace Nautilus in the above guide?**
I haven't tried this with any other file manager, so I wouldn't know. If you get this to work with another file manager, please reply to this with how you did it and I will add it to this guide!

**_Special thanks to:_**
**Pendrive Linux**, for their excellent howto for getting Ubuntu 7.10 on a USB drive, for making the archive which makes Ubuntu persistant, and for writing the tutorial which this guide is based off of.
**Ubuntu**, for their great distrobution.
**The members of Ubuntu's forums**, for helping me piece together how to do this and for using this guide. :)

**_UPDATES:_**
**2/1/08**: Updated the guide to include how to do persistance.

**Other projects**
There are a few projects out there now which try to create a wizard. One is called [LiveUSB]("https://launchpad.net/liveusb"), the other [UNetBoot]("http://unetbootin.sourceforge.net/"). I would recommend this howto if you want to do a custom distro, for example, or if you want the accomplishment of doing it yourself. ;)

---

### Post by K.Mandla on 2007-12-25
Moved to Installation and Upgrades.

---

### Post by smartboyathome on 2008-02-01
*bump*
I updated this guide to include how to make a persistant LiveUSB, and to make some steps clearer. Please don't hesitate to reply if you need any help. :)

---

### Post by Stuki on 2008-02-01
Does it work for xubuntu as well?

---

### Post by smartboyathome on 2008-02-01
Like it says in the italicized text above, yes it should. Any ubuntu-based distro should work with this.

---

### Post by Stuki on 2008-02-02
Oh... Sorry, I somehow missed it.

---

### Post by smartboyathome on 2008-02-02
Its fine, we all do that sometimes. ^^

---

### Post by Pumalite on 2008-02-02
Your link to download 'this archive' doesn't work.

---

### Post by smartboyathome on 2008-02-02
Thanks, its fixed. :)

---

### Post by Pumalite on 2008-02-02
For something a little more creative, there is this too:

[http://ubuntuforums.org/showthread.php?t=647321](http://ubuntuforums.org/showthread.php?t=647321)

---

### Post by smartboyathome on 2008-02-03
> **Pumalite said:**
> For something a little more creative, there is this too:

[http://ubuntuforums.org/showthread.php?t=647321](http://ubuntuforums.org/showthread.php?t=647321)

Yes there is, though that does take a little more space on the USB drive, and if your drive is 2GBs, you might be a little cautious about how many MBs are used up. ;)

---

### Post by probono on 2008-05-22
Hi all, I am working on a GUI to make things really simple. This tool creates a bootable Live USB medium from a running Ubuntu Live CD. It was made in response to Ubuntu Brainstorm idea #16.

[IMG]http://klik.atekon.de/liveusb/screenshot.png[/IMG]

It performs the following actions:

    * Detects available USB sticks (using HAL)
    * Partitions USB stick with 1 partition
    * Sets partition bootable
    * Writes MBR to USB stick
    * Formats partition FAT16
    * Installs bootloader (syslinux) to partition
    * Writes bootloader configuration file
    * Copies necessary files from running Live CD to USB stick
    * Sets language and keyboard of USB Live system to match running Live CD
    * Optionally: Downloads and integrates Adobe Flash Player

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)
#liveusb on freenode

---

### Post by smartboyathome on 2008-05-22
Perhaps you can make it so that you may also run it from a current Ubuntu install by letting the user choose the ISO image?

---

### Post by tuxcantfly on 2008-05-26
> **smartboyathome said:**
> Perhaps you can make it so that you may also run it from a current Ubuntu install by letting the user choose the ISO image?

UNetbootin at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) does just that, and additionally can be run from both Windows and Linux.

---

### Post by smartboyathome on 2008-05-26
Cool, adding both projects to the howto. :D

---

### Post by tuxcantfly on 2008-05-29
> **tuxcantfly said:**
> UNetbootin at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) does just that, and additionally can be run from both Windows and Linux.

FYI, I just posted a simple, screenshot-based howto on creating liveUSB drives using UNetbootin at [http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

---

### Post by MadsRH on 2008-05-31
This is just what I've been looking for!!! Great work **probono**

---

