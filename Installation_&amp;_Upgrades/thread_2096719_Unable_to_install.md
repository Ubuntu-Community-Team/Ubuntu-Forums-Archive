---
title: "Unable to install"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by inteldesign258 on 2012-12-20
I have been using a live usb now for two years and am finally experiencing the same problems discussed in this post:

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) "Unable to find a medium containing a live file system"

(initramfs)

So I downloaded an upgraded .iso  "ubuntu-10.04.4-desktop-amd64" the original .iso is ubuntu-10.04.3-desktop-amd64" With this new .iso how can I use it to repair "10.04.3 liveusb?
Can this be achieved in Busybox at the (initramfs) prompt? My second point is this...I have downloaded the file "bootinfoscript-061.tar" Can the script be run or created inside or at the initramfs prompt? :icon_frown: 
My host OS is Windows 7 on an ASUS X55a notebook!

---

### Post by oldos2er on 2012-12-20
Post moved to its own thread.

---

### Post by oldfred on 2012-12-21
You need to have a working Linux - install, liveCD or flash to run the bootinfo script. I usually suggest Boot-Repair as it is a gui and runs bootinfoscript plus more info. You can download Boot-Repair into a Linux you have or download a full repair ISO to install to DVD or flash.

If just a live install, do you have anything saved with persistence? 
Or after many uses perhaps flash drive has failed? 
Or maybe just a chkdsk if FAT32?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

---

