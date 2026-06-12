---
title: "Cant get it to install to hardrive only usb"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by Tynarium on 2013-02-14
I am trying to install ubuntu from my usb to my hard drive but instead it just keeps installing to the usb. I don't know where to select the hard drive to make it install properly.

---

### Post by newjersian1 on 2013-02-15
These are instructions to dual boot windows and ubuntu. 
If you only want ubuntu, then go through these instructions up to step 4. there will be a choice saying something like, "erase everything and install Ubuntu." Only choose this if you are certain that there is nothing you want is saved on your computer. 



[SIZE="4"]Install Ubuntu[/SIZE]
1. Download an Ubuntu LiveCD image (.iso) from Ubuntu Downloads and burn it to a disc (see BurningIsoHowto).

2. Insert the LiveCD into your CD-ROM drive and reboot your PC.

3. If the computer does not boot from the CD (e.g. Windows starts again instead), reboot and check your BIOS settings by pressing F2, F12, Delete, or ESC. Select "boot from CD".

4. Proceed with installation until you are asked this question: "How do you want to partition the disk?".

5. If you have already partitioned the disk and left space for Ubuntu, install it to that and then follow the rest of the steps.
Otherwise, choose one of the next two steps.

     6. a. [SIZE="4"]Automatic partition resizing[/SIZE] (recommended)

     6. b. Choose the first option, which should say "Install them side by side, choosing between them each startup".

     6. c. Specify the size of the new partition by dragging the slider at the bottom of the window.

     6. e. Click on "Forward".

     6. f. Continue on to Finishing Ubuntu Installation

   7. a. [SIZE="4"]Manual partitioning[/SIZE]

   7. b. Choose "Manually edit partition table".

   7. c. Listed will be your current partitions.

   7. d. Select the partition you want to resize and press Enter.
  
   7. e. Select "Size:", press Enter.

   7. f. Select Yes, press Enter.

   7. g. Type in a new size in gigabytes for your partition, it's recommended you free up at least 10 GB of free space for your Ubuntu install. Press Enter when happy with your changes. It may take some time to apply the changes.


   7. h. Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value).

   7. i. Create a partition for your Ubuntu installation.

   7. j. Create other partitions if necessary: see DiskSpace


   7. k. Select "Finish partitioning and write changes to disk".

---

