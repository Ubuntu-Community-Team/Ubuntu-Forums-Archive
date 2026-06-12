---
title: "No such partition: Grub Rescue"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by AlanR917 on 2013-01-28
Hello everyone, I recently deleted my ubuntu partition through windows, and then installed windows 8. Now whenever I restart my pc, it says ```
no such partition
```
```
grub rescue>
```

I just want my windows 8 back, is there any way i can fix this without a recovery disc (I downloaded windows 8 through their site) and still have my data? thank you!

---

### Post by srekcahrai on 2013-01-28
To repair it you will need bootable Windows 8 media (DVD, flash). After booting from it there should be repair option. You need to repair your startup.

---

### Post by oldfred on 2013-01-28
While best to have a Windows 8 repairCD or Flash drive, you can restore a Windows work alike boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

            Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
Or from Ubuntu liveCD.
       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by AlanR917 on 2013-01-28
Thank you!!!!!! Its back up and running and I didnt lose my files. You rock!

---

### Post by srekcahrai on 2013-01-29
Sweet! Now you can post your thread as [SOLVED]

---

