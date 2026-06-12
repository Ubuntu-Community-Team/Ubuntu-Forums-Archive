---
title: "[SOLVED] Can't boot from USB stick"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2008-11-03
I used intrepid's new USB startup drive creator.  It worked fine, but I can't seem to boot off the USB stick.  I tried two machines, a MacBook Pro, and a Dell Optiplex 745.  The MacBook only showed the main hard drive as bootable.  The Dell Optiplex just froze up on a black screen when I try to boot off the USB stick.

Any help would be appreciated.

---

### Post by suewolf on 2008-11-03
I have a pair of 2 GB flash drives, both formatted FAT32. The USB Startup Drive creator in Intrepid (live CD) crashes when I use the first one. The second one installs fine, but I get a black screen with BOOT ERROR when I try to boot from it. My PC boots from other flash drives, using previous Linux distros.

---

### Post by CaptSaltyJack on 2008-11-03
Sounds like a bug that needs squashing. ;)

---

### Post by suewolf on 2008-11-03
This method from pendrivelinux.com worked just great, as far as I can tell:

1. Download the Ubuntu 8.10 ISO and burn it to a CD
2. Restart your computer, booting from the Live CD
3. Insert a 2GB or larger USB flash drive
4. Open a terminal and type the following into the terminal window:

wget pendrivelinux.com/downloads/u810/u810.sh

chmod +x u810.sh && sh u810.sh

5. Follow the onscreen instructions
6. Once the script has finished, reboot your computer and set your BIOS or boot menu to boot from the USB device

Their web site is 

[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

or 

[http://tinyurl.com/6njspg](http://tinyurl.com/6njspg)

---

### Post by CaptSaltyJack on 2008-11-03
Thanks for the info!

Can anyone else confirm this (Intrepid's built-in USB startup disk maker) is not working properly?

---

### Post by C.S.Cameron on 2008-11-03
Usb-creator still seems to have a few problems.
Works great for me with a 2G Kingston, but not with 4G or 8G Kingstons.

Installs on all of them ok but the 4G and 8G don't boot.
get everything from "grub_" to busybox with (initramfs)

---

### Post by CaptSaltyJack on 2008-11-03
Weird, why would the USB drive capacity make a difference, I wonder?

---

### Post by C.S.Cameron on 2008-11-03
Have tried dozens of times using usb-creator to install to a 4 gig Kingston, without success.
This is what finally worked:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum "Stored in reserved extra space", (128 MB).
Pressed "Make Startup Disk".
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted casper-rw.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

### Post by C.S.Cameron on 2008-11-03
Oops, double post.

---

### Post by CaptSaltyJack on 2008-11-06
> **C.S.Cameron said:**
> Have tried dozens of times using usb-creator to install to a 4 gig Kingston, without success.
This is what finally worked:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum "Stored in reserved extra space", (128 MB).
Pressed "Make Startup Disk".
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted casper-rw.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

This worked great, thanks!  The only thing I found confusing is the "delete casper-rw" step.  There's actually a FILE called casper-rw on the "disk" partition.  I was looking at the casper-rw partition and wondering how/why I would delete it. :)

---

### Post by dryicebomb on 2009-02-02
> **C.S.Cameron said:**
> Have tried dozens of times using usb-creator to install to a 4 gig Kingston, without success.
This is what finally worked:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum "Stored in reserved extra space", (128 MB).
Pressed "Make Startup Disk".
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted casper-rw.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

All of this worked for me, except i had to do one additional step to make it work. From the terminal i had to type install-mbr /dev/sdX (X being the letter assigned to my USB drive)

---

### Post by Rubicon421 on 2009-02-05
I think I could follow this if I had to, but is there an easier way to get around this problem? I made a usb start up disk from a live cd of 8.10 on an 8GB PNY jump drive. Installed fine but wont boot. My bios dont support booting from USB so I downloaded and burned the iso for the usb boot disk and restarted with both disks in. I got the menu shown in the screenshot above, the one that says press enter to boot from usb. Then I get the error about busybox and initramfs. Tried the same usb and boot disc in another machine and got the same thing.

---

### Post by caraboy on 2009-02-16
I used a 4GB usb flash drive formatted in Windows (FAT32) and it did not work the first time. I got an error about "invalid or damaged bootable partition".

Managed to make it work this way:
1. Install Gparted
2. In Gparted, erase the existing partition (first unmount the stick). 
3. Make a new partition on your stick, fat32.
4. Now you can use the **System > Administration > Create a USB startup disk** option. It will boot this time.

Hope it works, for me it did! :D

---

### Post by CaptSaltyJack on 2009-02-16
> **dryicebomb said:**
> All of this worked for me, except i had to do one additional step to make it work. From the terminal i had to type install-mbr /dev/sdX (X being the letter assigned to my USB drive)

Confirmed - I had to do install-mbr to get it working, too.

---

### Post by malexous on 2009-02-18
> **caraboy said:**
> I used a 4GB usb flash drive formatted in Windows (FAT32) and it did not work the first time. I got an error about "invalid or damaged bootable partition".

Managed to make it work this way:
1. Install Gparted
2. In Gparted, erase the existing partition (first unmount the stick). 
3. Make a new partition on your stick, fat32.
4. Now you can use the **System > Administration > Create a USB startup disk** option. It will boot this time.

Hope it works, for me it did! :DThanks! Luckily I searched for my problem before posting a new thread.

I was doing the same as you with a 2GB flash drive and getting the same error. I used Gparted on the Live CD and everything works flawlessly :D

---

### Post by rasmus91 on 2009-02-22
> I used a 4GB usb flash drive formatted in Windows (FAT32) and it did not work the first time. I got an error about "invalid or damaged bootable partition".

Managed to make it work this way:
1. Install Gparted
2. In Gparted, erase the existing partition (first unmount the stick).
3. Make a new partition on your stick, fat32.
4. Now you can use the System > Administration > Create a USB startup disk option. It will boot this time.

Hope it works, for me it did! 

THANKS SO MUCH! I have a 4 GB TDK flash drive. And i did this, and it works when i follow your guide. :)

---

