---
title: "New user trying to boot from USB onto labtop"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by damian22 on 2016-01-08
Hi guys, im a brand new linux user, and I decided to try ubuntu, I need linux to do my masters project and have switched for the first time

I took some computer science classes and have been coding for a year and a half so I have a tiny bit of knowleadge.

I decided to use one of my labtops to run ubuntu, to not loose windows i decided to change hardrives, bought a brand new one, I made sure to install it well. Now i download the iso ubuntu file on a usb key.

I used pendrive linux and universal usb installer to install ubuntu on the usb and make it bootable.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


Now the problem I am having is that i get to the ubuntu installation page but it doesn't want to see my new hardrive, it only sees my usb is running and says that I have total space of 2 gig when my hardrive is 120 gigs.

I went to the terminal and used sudo fdisk -1 and df-h to see what are my hardrives space and it sees only my usb from what i can tell.

Now reading on internet some people say to use gpart and some other things, but this goes beyond my knowledge and would like not to procceed further until Im sure im doing the right thing, does anyone know why ubuntu wouldn't see my new hardrive.

Also i tried unscrewing and checking that i plugged my hardrive well I followed a youtube video and Im preaty sure the hardrive is well connected.

Any help would be appreciated

---

### Post by yancek on 2016-01-08
You didn't indicate which windows version you are using.  Makes a difference.  Windows 8 and newer use UEFI/GPT in a default installation so post what you have.
Did you check to see if the drive is recognized in the BIOS?

> Now i download the iso ubuntu file on a usb key.

This may be confusion in terminology?  You download the Ubuntu iso to your hard drive.  You then use software such as pendrivelinux to put the iso on a flash drive to be bootable then reboot the computer to install.  Which installaiton type did you select when installing Ubuntu?  If you have windows 8 or newer, did you turn off anything related to hibernation or fast boot?

---

### Post by Bucky Ball on 2016-01-08
yancek: OP states they have taken the Windows disk out of the machine and are trying to install on a brand new, unused drive, unless I'm misunderstanding the first post. :)

@OP: Prior to creating the install media, wipe all partitions from the USB dongle and format it as FAT32. Boot from that and 'Try Ubuntu'. This will not change anything on you hard drive. Once at a desktop, launch Gparted. What does that show on the hard drive, if it shows the hard drive?

---

### Post by damian22 on 2016-01-09
Yes to precise Im using a brand new hardrive that fresh it doesn't have any os on it, previously i was running 8.1 and i disabled fast startup before starting the install process.

Just to ask how do you wipe partitions on a drive is there a tutorial somewere i don't even know really what is a partition and how to wipe it.

I also read to be carefull using gparted as it can screw up the launch

---

### Post by yancek on 2016-01-09
Just to make sure we are understanding your situation, you have only the new hard drive attached to your laptop?
Did you check the BIOS to see if the new drive (120GB) is shown.  If it doesn't show in the BIOS, you will not be able to install to it.
Open a terminal from the flash drive and select Erase disk and install Ubuntu if the drive shows and the new drive is the only one attached.
Using GParted is explained in detail in their manual at the link below.  To open GParted, open a termnal when you boot the flash drive and type:  sudo gparted (hit the enter key) and this should show a graphical image of drives/partitions.  There is a drop down menu if you click the down arrow in the upper right of the window which should show the different drives.   


[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by oldfred on 2016-01-09
You mention Windows 8, was that pre-installed? If so then you have a newer UEFI based system than can be booted in 3 boot modes. UEFI with secure boot, UEFI without secure boot and CSM/BIOS/Legacy boot modes. Only the 64 bit version of Ubuntu will work in UEFI mode.

Some combinations of USB installers and flash drives, and some systems just seem to have issues. 
Confirm that download is valid with md5sum, and try different installers.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

From Windows many have had good success with Rufus.
       How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html
[/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

[URL="http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html"]
[/URL]

---

### Post by damian22 on 2016-01-09
Thank you guys will try to do it

---

