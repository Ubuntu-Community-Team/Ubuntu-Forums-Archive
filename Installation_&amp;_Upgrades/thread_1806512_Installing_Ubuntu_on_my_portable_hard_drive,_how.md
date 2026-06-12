---
title: "Installing Ubuntu on my portable hard drive, how?"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by garycheng12 on 2011-07-17
First off, I am very new to Ubuntu, and quit using Ubuntu after trying it for several days. Right now, I am interested in the operating system because I plan on installing Ubuntu on my portable hard drive so that I can basically treat people's computer as my own by using their computer to boot my Ubuntu from the portable hard drive.

I was wondering what information I need to know before I attempt to install Ubuntu on the portable hard drive. Here are several questions to get started:

1. I've heard that ext4 file system is superior to the NTFS file system. If I install Ubuntu as an ext4 file system, can I freely transfer files between Windows (NTFS) and Ubuntu (ext4)? 

2. What are all the partitions I am responsible for when I install Ubuntu? I remember (from last year, when I experimented with the OS) that there are partitions like /home. Is it like Windows's version of "Program Files"? 

3. I can always change the size of all the partitions of Ubuntu as long as I have room, right? So I don't need to worry about reserving only 20 GB for Ubuntu for now and then expanding it to 60 GB if I plan to use it more and store my personal files?

4. Is there a way to make it so that every time I restart a computer (mine and any random computer available), it will show a menu where I can select which OS to boot, either Windows or Ubuntu, so that I don't have to manually alter the computer's BIOS in order to tell the computer to boot from the portable hard drive or the internal hard drive of the computer? I heard something about GRUB but I don't know what that is.

I only have these questions for now--once they are answered, I can proceed to installing Ubuntu and get started.

If memory serves, ubuntuforums.org is very active with people willing to provide whatever they can. I really hope I can get some answers from this thread, since I don't know any better place to ask my questions than here! I'll be refreshing this page every few minutes.

---

### Post by ManualSparrow on 2011-07-17
1. Ubuntu can see NTFS, but Windows cannot see ext4. So you can retrieve and move files to Windows computers but not the other way around. Which brings us to...

2. The /home "mount point" is where you keep your documents and settings. It may be advisable to partition your external drive into a / ("root"), /home, and a small "swap" partition equal of about 2-4 GB. You may want to make the /home mount point NTFS so you can read them without booting the OS.

3. Using this scheme, 20GB or less would be fine for the system, then there is the 4GB swap, and everything else is /home.

4. Ubuntu automatically installs the GRUB bootloader, which allows you to select an OS to boot (you still have to tell the BIOS which hard drive to boot from though). You wouldn't have to worry about that for a normal install, but since this is a "roving" installation there are caveats:

a. GRUB installs on the MBR, not on a partition, so you need to specify which hard drive you want to install it on. This will usually be called sdb (and the partitions will be sdb1,2,3, etc) inside of the GParted partitioning tool you will be using during the install (to access this while installing from your CD or USB, select "Something Else" when it asks you how you want to set up the partitions). If you specify sda (the normal hard drive) you will only be able to boot from that computer (and won't be able to boot anything if the external drive is not connected, because the config file is stored in the Ubuntu / partition).

b. Different BIOSes assign different numbers to their hard drives, so it might be that the GRUB loader won't be able to find your installation on some computers. I am trying to find a workaround for this right now myself, but one option might be the Universal Multiboot Installer from PenDrive Linux: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/). **(Someone should be able to point out if that is actually an issue).**

---

### Post by garycheng12 on 2011-07-17
> **ManualSparrow said:**
> 1. Ubuntu can see NTFS, but Windows cannot see ext4. So you can retrieve and move files to Windows computers but not the other way around. Which brings us to...

2. The /home "mount point" is where you keep your documents and settings. It may be advisable to partition your external drive into a / ("root"), /home, and a small "swap" partition equal of about 2-4 GB. You may want to make the /home mount point NTFS so you can read them without booting the OS.

3. Using this scheme, 20GB or less would be fine for the system, then there is the 4GB swap, and everything else is /home.

4. Ubuntu automatically installs the GRUB bootloader, which allows you to select an OS to boot (you still have to tell the BIOS which hard drive to boot from though). You wouldn't have to worry about that for a normal install, but since this is a "roving" installation there are caveats:

a. GRUB installs on the MBR, not on a partition, so you need to specify which hard drive you want to install it on. This will usually be called sdb (and the partitions will be sdb1,2,3, etc) inside of the GParted partitioning tool you will be using during the install (to access this while installing from your CD or USB, select "Something Else" when it asks you how you want to set up the partitions). If you specify sda (the normal hard drive) you will only be able to boot from that computer (and won't be able to boot anything if the external drive is not connected, because the config file is stored in the Ubuntu / partition).

b. Different BIOSes assign different numbers to their hard drives, so it might be that the GRUB loader won't be able to find your installation on some computers. I am trying to find a workaround for this right now myself, but one option might be the Universal Multiboot Installer from PenDrive Linux: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/). **(Someone should be able to point out if that is actually an issue).**

Hey, thanks for the answers. I just attempted to install Ubuntu on the portable hard drive, but I came across something that said "Install Bootloader on device"... what does that mean and where should install it?

---

### Post by lmarmisa on 2011-07-17
> **garycheng12 said:**
> Hey, thanks for the answers. I just attempted to install Ubuntu on the portable hard drive, but I came across something that said "Install Bootloader on device"... what does that mean and where should install it?

You should install the GRUB loader in the MBR of your external (portable) hard drive. Do not install it in your internal hard drive!!!!.

---

### Post by ManualSparrow on 2011-07-18
The bootloader is GRUB - it is where you select what OS to boot. As I said and the post above cautions, make sure you install it on the external drive - which will probably be identified as "sdb." Don't select any of the partitions on it, like "sdb1," or install it on the internal drive, which would be sda most likely.

You should be able to identify which is which by the manufacturer/model number, but if not, ask here.

---

### Post by garycheng12 on 2011-07-18
Thanks, everyone. I've successfully installed Ubuntu on my portable hard drive and was able to boot into Windows by unplugging the hard drive and changing the BIOS to to have priority on removable devices over internal hard drives.

The interface of Ubuntu is clean, but right now, I'm trying to make it as familiar of a place as it is with Windows--I feel like maybe it's over-simplistic, but I will have to get used to it and see.

---

