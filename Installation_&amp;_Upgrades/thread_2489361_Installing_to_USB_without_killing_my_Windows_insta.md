---
title: "Installing to USB without killing my Windows install"
date: 2023-07-27
forum: Installation &amp; Upgrades
---

### Post by electronproton on 2023-07-27
Hi Everyone,

This is my first post here. I've been using Linux on and off for many years. I've usually run from a USB drive but after messing up many windows installs when trying to install Linux I resorted to removing my laptop's SSD before attempting an install to USB, to guarantee Windows would still be ok. 

Now that laptop is no more and I have a new Surface Laptop Go 2 which I really like but I can no longer easily remove the SSD, so can someone please give me a step-by-step guide to using the manual partitioning option of the Ubuntu set up procedure so that I can install to USB (either USB flash drive or an SSD in a USB enclosure) without touching my internal SSD and Windows.

I would really appreciate some guidance with this as I  want to have Ubuntu as my main OS but still have Windows. I can't dual boot as I went for the cheapest model with a small SSD.

Thanks for any advice offered. 
Rich

---

### Post by tea for one on 2023-07-27
Many modern PCs/Laptops have a UEFI setting where you can isolate or de-activate an SSD without physically removing it.
Have a look at your UEFI firmware settings.

---

### Post by ubfan1 on 2023-07-27
Which Ubuntu release do you want to install?  Ubuntu 22.04 (LTS) still had launchpad bug 1396379, grub installs to wrong device (internal disk), but Ubuntu 23.04 will actually install grub to where you indicate (I assume you want the USB drive).

---

### Post by electronproton on 2023-07-27
Thanks for the suggestion. There's nothing like that in my UEFI. The settings are actually very limited

---

### Post by electronproton on 2023-07-27
I will be using the latest version but I don't know how to use the manual partitioning bit

---

### Post by tea for one on 2023-07-27
> **electronproton said:**
> Thanks for the suggestion. There's nothing like that in my UEFI. The settings are actually very limited
That's a bit surprising.
I was led to believe that these Microsoft Surface devices were quite sophisticated.

Anyway, have a look at this link for more info about your type of PC.
[https://github.com/linux-surface/linux-surface](https://github.com/linux-surface/linux-surface)

---

### Post by electronproton on 2023-07-28
The UEFI only has an info page, a security page with UEFI password, secure boot, and multi threading options, a boot configuration page with a few options but nothing about disabling internal drive, then pages for date and time, secured core, and exit.

---

### Post by guiverc on 2023-07-28
It'll be helpful if you're specific with details.

Ubuntu 23.04 is the *latest* version, if you're asking about Desktop, then two installers are possible (`ubiquity` and `ubuntu-desktop-installer`, with the second being the default ISO offered at download unless you select and use the *alternate*).

Ubuntu 23.04 Server uses the `subiquity` installer, with most desktop *flavors* using `ubiquity` except two which use `calamares`.

You select which installer you'll use at download time, when you select which ISO you download.  Are you sure you want the *latest* though?  Ubuntu 23.04 is only supported until January 2024, where as using the LTS or *long term support* release will have years of support.

Do note the ISO/installer defaults for the LTS differ to 23.04; thus being specific on what you want to use is helpful for those trying to give advice.  (Ubuntu 22.04 LTS desktop defaulted to `ubiquity` as the *primary* ISO, with `canary` as `ubuntu-desktop-installer` was then known as the *alternate* ISO; I'd not recommend using the *canary* installer if you opt to use 22.04.2 or earlier).

---

### Post by ActionParsnip on 2023-07-28
You'll need an install USB and a destination USB. Just set the file systems on the USB stick. The dual boot should be managed for you

---

### Post by ActionParsnip on 2023-07-28
As with any system change. Run a final full backup to protect your data

---

### Post by yancek on 2023-07-28
It seems as if you are not familiar with Linux device/partition naming conventions and filesystems.  If you use the Ubuntu USB, you can open a terminal and run commands such as:

sudo fdisk -l and sudo parted -l which will list the devices and partitions as well as the filesystem and size of the device.  This should help you to decide which drive and partition to use.  If you are using a USB to install to another USB, it would simplify the process for you if they are of different sizes to avoid confusion.  The link below has a pretty detailed explanation of using the Something Else option to install Ubuntu.  Note that if you create a new partition table on a device as suggested there, it will erase all data on the device!

[https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/](https://www.linuxteck.com/how-to-install-ubuntu-22-04-lts-step-by-step/)

---

### Post by electronproton on 2023-07-28
Ah sorry. I didn’t realise there were installer options. So far I’ve just booted from live usb to the desktop then run the installer from there. At the manual partitioning page the internal disk is marked for format and i cant uncheck the boxes. I also can’t select the usb drive as the location for the boot software. 

FYI I’m booting from a USB flash drive and running Live desktop from there. I have an SSD drive in a USB enclosure which is where I want to install Ubuntu so that I can boot from that when I want to but still boot windows from internal disk. 

I opted for the latest release because in the past I’ve found the latest one to have best hardware support but I haven’t tested that opinion for a long time.

---

### Post by tea for one on 2023-07-28
_Full Install (inc Grub) to Second Drive or External USB Drive_

Backup all personal data
Attach USB containing Ubuntu 23.04 installer.
Attach new target disk, which has gpt but without partitions.
Boot into a live session of Ubuntu 23.04 
Open Gparted, remove esp and boot flags from sda1 or nvme0n1p1 (the internal disk EFI partition).
Close Gparted.
Start the Ubuntu 23.04 installation process.
When you reach the partition option > Choose Erase Disk and Install Ubuntu.
Select target disk 
Allow installer to create partitions
Device for bootloader installation is your target disk (not a partition)
Pause the installation and open Disks.
Double-check the status of the internal disk EFI partition > it should not be mounted.
Continue and you should see a dialogue box similar to:- 
> If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.
The partition tables of the following devices are changed:
SCSI3 (0,0,0) (sdb)
The following partitions are going to be formatted:
partition #1 of SCSI3 (0,0,0) (sdb) as ESP
partition #2 of SCSI3 (0,0,0) (sdb) as ext4

Continue installation (you must have an ESP and a system partition)
After completion of the installation, choose &#8220;Continue testing&#8221;.
Open Gparted again, restore esp and boot flags to internal disk.
Close all open applications and power off.

---

### Post by electronproton on 2023-07-29
Thank you for the detailed instructions Tea for one. I followed them but still no luck. On the manual partitioning page the far right column &#8220;format&#8221; has check boxes. The check boxes for the internal drive partitions are filled in solid grey and i can&#8217;t deselect them. Further down there&#8217;s a menu showing device for boot loader installation. All drives show up here, that&#8217;s usb stick plus usb ssd plus internal ssd. None of them are available. Everything is greyed out. When I click next it says about formatting nvme internal drive so I stop there. Could this be some kind of Microsoft feature unique to their surface devices?

---

### Post by tea for one on 2023-07-29
You chose "Manual partitioning" where I suggested
> When you reach the partition option > Choose Erase Disk and Install Ubuntu.
This option will allow you to select your second or external drive.
Take care to choose the correct device.

---

### Post by electronproton on 2023-07-29
Ah sorry, my mistake. I’ll try again.

---

### Post by electronproton on 2023-07-29
Thank you to everyone who replied. It worked at last. I followed you advice correctly this time tea for one and it worked. It’s nice to be away from windows and I’ll try to learn more about Linux’s file system and more.

---

### Post by tea for one on 2023-07-29
I have noticed that the Manual Partitioning section of Ubuntu 23.04 installer does not allow complete control over external disks.
For example, there is no option to create an ESP?
You can use Gparted in advance to create partitions but "Erase Disk and Install Ubuntu" is probably a bit easier for those who are unfamiliar with partition terminology.

Anyway, pleased to have helped.
It is a nice gesture to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

