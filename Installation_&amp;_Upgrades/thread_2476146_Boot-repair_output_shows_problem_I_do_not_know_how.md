---
title: "Boot-repair output shows problem I do not know how to fix"
date: 2022-06-17
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-06-17
Boot repair summary is at [https://pastebin.ubuntu.com/p/ff99J4JMgs/](https://pastebin.ubuntu.com/p/ff99J4JMgs/) 

Boot repair output on screen says reboot your computer, but apparently there is no boot loader.

Also, there is a problem with sda11.  It is an NTFS partition.  How do I view what is on that partition?

It may be that I need to reinstall the Unity version of Ubuntu.  Nothing on the Ubuntu partition that isn't on other PC's.

This is a dual-boot with Win 10.  I was putting my data files in exfat partitions so that they would be accessible to both OS's.  I checked those and they were accessible by both OS's.  Then I reformatted the old MyChemistry partition to exfat and then PC would not boot.

Thank you.

John

---

### Post by cigtoxdoc on 2022-06-17
I was able to get the system started by playing around with boot order.  I got rid of the files in sda11.  More work will be needed.  John

---

### Post by yancek on 2022-06-17
You appear to have tried to install Ubuntu more than once as you have both a Legacy install as according to the info beginning at line 58, you have grub code in the mvr pointing to grub on sda12.  You also have an EFI partition (sda10) which is useless and not needed on a Legacy install such as yours.  In your BIOS firmware you need Legacy/CSM enabled to boot which you apparently now have if you can boot Ubuntu.

>  Also, there is a problem with sda11.  It is an NTFS partition.  How do I view what is on that partition? 


The most common reason for a Linux OS to not see a windows partition is because windows is using the default hibernation and Linux won't mount the partition in that case so it would not be accessible.  Go to the power settings in windows and check hibernation and if it is on, turn it off and you should be able to access it from Ubuntu.

---

### Post by oldfred on 2022-06-17
Normally NTFS is suggested as it has a journal which can help in case you need repairs.

Your sda5 on line 105 shows an error. See if some Windows tools may fix it.
>  Mounting failed:   ERROR: illegal UTF-16 sequence.

You have a newer UEFI based system, but Windows in old BIOS/MBR configuration.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8.
But since conversion from MBR to gpt will totally erase drive, probably best to stay with BIOS/MBR for now.
But then you Ubuntu install also must be MBR.

Only if planning new drive or major changes should you then consider new UEFI installs for both Windows & Ubuntu & then restore of data only from your normal backups.

---

