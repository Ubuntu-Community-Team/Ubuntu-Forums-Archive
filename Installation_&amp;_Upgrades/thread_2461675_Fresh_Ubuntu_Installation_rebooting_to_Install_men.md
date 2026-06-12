---
title: "Fresh Ubuntu Installation rebooting to Install menu"
date: 2021-05-05
forum: Installation &amp; Upgrades
---

### Post by loganydid on 2021-05-05
I am having a heck of a time trying to install Ubuntu 20.04 on my computer. The computer I am using is a dell latitude 14 rugged 5414. I purchased a new 1TB SSD and inserted it into the slot in the side of the computer. I downloaded the most recent ISO of Ubuntu and used Rufus to load it on a removable USB Flash Drive. I put in the flash drive, entered the BIOS, and set the boot order to boot from the USB. I followed all the on-screen instructions and 12hrs later I'm greeted with a dialog that tells me to restart, so I do.

When it boots up I get a black screen that says "Invalid partition table!" if I hit enter it boots back up to the installation menu. It does this even without the installation medium plugged in. I have tried doing this like 3 times. Is there something that I'm missing? Has anyone else encountered this problem beore?

---

### Post by yancek on 2021-05-05
Installing Ubuntu should not take more than 30 minutes on a recent computer.  Did you do an md5checksum on the Ubuntu iso you downloaded before trying to install?  Expllained at the Ubuntu site below.

[https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64)

To post more information on the system, go to the site below and use the 2nd option explained on that page to download and run boot repair.  Do not try to make repairs but select the option to Create BootInfo Summary and post the link you get when it finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2021-05-05
Please tell us the options you chose during the installation process. Was it erase disk and install Ubuntu? Was it Something Else? Did you have a Windows operating system on that machine? Do you still have it?

You say it boots back to the installation menu even with the USB memory stick removed. That sounds like an impossibility. Unless you burned the install ISO image to a drive other than the USB memory stick. Please confirm that it is not going back to some menu from the motherboard's UEFI settings utility offering a drive option to boot from.

Regards

---

### Post by loganydid on 2021-05-05
Yes, I selected "Install Ubuntu" so it should erase the disk and install. This is a new hard drive straight out the box, no OS installed, and it is the only drive on the computer. One of the things I have tried in this process is burn the boot iso directly to the hard disk but since then I have formatted it using the windows disk management utility I figure that shouldn't be the issue.

Other options I selected include "Normal installation", "Download updates while installing Ubuntu", and "install third party software..."
When it reboots it boots right back into the same installation menu, regardless of boot medium.

---

### Post by loganydid on 2021-05-05
> **yancek said:**
> Installing Ubuntu should not take more than 30 minutes on a recent computer.  Did you do an md5checksum on the Ubuntu iso you downloaded before trying to install?  Expllained at the Ubuntu site below.

[https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64)

To post more information on the system, go to the site below and use the 2nd option explained on that page to download and run boot repair.  Do not try to make repairs but select the option to Create BootInfo Summary and post the link you get when it finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Thanks, I will try these when I get home later today. I might also try completely formatting the drive and deleting partitions to start fresh

---

### Post by loganydid on 2021-05-05
Ok, I formatted the drive using windows disk manager, reburned the iso on the usb drive, and now I am waiting for ubuntu to install. It has been sitting for about 2.5 hours now I'll let you know when it is complete.

---

### Post by corradoventu on 2021-05-06
If you select 'erase disk and install ubuntu' you don't need another format, but ubuntu install should not take more than 15-30 minutes. 
If you select 'download updates during install' and you have a very slow internet access the time for downloading the updates may count.

---

### Post by tea for one on 2021-05-06
> **loganydid said:**
> I formatted the drive using windows disk manager

Which file system did you choose?
Windows tools cannot create suitable partitions for Linux installations unless you have used another utility.

Have you seen this [https://help.ubuntu.com/community/UEFI?](https://help.ubuntu.com/community/UEFI?)

---

### Post by loganydid on 2021-05-06
> **corradoventu said:**
> If you select 'erase disk and install ubuntu' you don't need another format, but ubuntu install should not take more than 15-30 minutes. 
If you select 'download updates during install' and you have a very slow internet access the time for downloading the updates may count.

When I woke up this morning it was still going around 13 hours later. I did select 'download updates during install' which definitely makes it take longer but regardless I have to let it go overnight because it takes so long.

---

### Post by loganydid on 2021-05-06
I just used the disk manager tool to delete all the partitions and format the disk. I was doing this as a precautionary measure but like corradoventu said, it shouldn't matter. If I select select "Erase Disk and Install" it should format and repartition the disk as necessary, right?

---

### Post by loganydid on 2021-05-06
BTW I checked the checksum and the iso looks good.

---

### Post by loganydid on 2021-05-06
Holy cow it's still going!!!
When I checked on it it appeared to have gone to sleep. It says "configuring hardware" now and there is still text scrolling on the terminal so I guess it's ok?

---

### Post by loganydid on 2021-05-07
Ok, this morning it was finished so I rebooted the computer leaving the boot medium in and now I'm at a screen with a bunch of errors:
[https://ibb.co/DzzRcP9](https://ibb.co/DzzRcP9)

---

### Post by grahammechanical on 2021-05-07
I am going to ask a stupid question. Some among us say, there are no stupid questions but I am going to ask one anyway.

The Ubuntu installation process requires user interaction. Information such as User name; User password; Location; setting up an internet connection (maybe). Sometimes, during the later part of the process we may be asked to make certain choices. If we do not respond the stupid computer program just waits and waits. For most of the process all the work is done in computer memory. It is not written to disc until late in the process. Trying to re-start the installation process could possibly cause a reboot of the machine which would bring us back to the installation menu.

Did you start the installation and then leave? Did you set a User name and password? May I make a suggestion? When you try installing again run the live session - Try Ubuntu. Then open System Settings and turn off Blank screen. It is under the Power tab. It has been my experience that during the installation process the screen will blank and when the installer asks for input I miss seeing the dialog box. And then I wonder why the installation is taking so long. An alternative is to move the mouse around a bit every so often. In this way I do not miss any requests for user input.

We can select Install Ubuntu from an icon on the live session desktop.

Regards

---

### Post by loganydid on 2021-05-11
After formatting the disk, reburning the image to the usb drive, and reinstalling ubuntu it still boots to the installation menu.
 I ran the boot repair and the result is below

[http://paste.ubuntu.com/p/JhvZKyhV4v/](http://paste.ubuntu.com/p/JhvZKyhV4v/)

---

### Post by tea for one on 2021-05-12
It looks like you haven't installed Ubuntu.

[COLOR="#0000FF"]Line 15[/COLOR] - 0 (zero) OS detected
[COLOR="#0000FF"]Line 60[/COLOR] - sda1 ntfs is a Windows file system

---

### Post by ajgreeny on 2021-05-12
Yes, the only operating system detected by that script was the live one on the USB and that is not running in UEFI mode; so far you have installed nothing.

So try again booting to the USB but this time make sure it starts in UEFI mode; usually there are two instances of the USB to choose from in the device list, one with UEFI at the start the other without UEFI; make sure you choose the UEFI one, that is very important.

Now choose to run the live OS, listed as "Try Ubuntu without installing" or similar description and when that starts use gparted to delete the ntfs partition on the hard disk and leave it as unallocated space.

Now when you choose to install the OS you can again try the "Use whole disk" option and let the installer create the partitions needed, an EFI partition for the UEFI and grub bootloader files which will be about 500M fat32, and the rest as ext4 for the OS itself.
Apart from the computer name (hostname), your username (must all be in lowercase), and password for the user, there is not much else to choose between.  

As I have never had an nvidia graphics system which needs a driver installed as soon as possible, I never install updates, extra drivers or other packages during installation but wait until the OS is installed and rebooted then add what is needed/wanted for my own use of the system.

---

### Post by loganydid on 2021-05-22
Sorry for the late reply, 

Thanks for the advice, the issue I'm running into is that with the USB in, the computer boots like it should (all the way to the login screen). 
Without the USB in it boots to the "Install Ubuntu" dialog which is really blowing my mind.

I think I'm going to start from ground zero and reburn ubuntu to the USB and follow the steps you outlined.

---

### Post by loganydid on 2021-05-22
ok, I reburned ubuntu to the USB and I booted into the "try ubuntu" environment ensuring it started in UEFI mode
I started GParted to delete the ntfs partition but I dont see a ntfs partition. See below for screenshots of what I'm seeing in both the 32gb flashdrive and the 1tb SSD.

[https://ibb.co/d070T5M](https://ibb.co/d070T5M)
[https://ibb.co/FB63S8S](https://ibb.co/FB63S8S)

Should I just continue to installation?

---

