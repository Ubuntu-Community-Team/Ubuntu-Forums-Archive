---
title: "Install stuck on partitions table"
date: 2019-11-13
forum: Installation &amp; Upgrades
---

### Post by lathorne on 2019-11-13
I'm trying to install Ubuntu 19.10 on a new Dell XPS 13 7390. I want to overwrite Windows and just run Ubuntu. I get stuck in the installation process because it skips the step where it asks me if I want to erase the disk and install Ubuntu or manually assign the partitions. Instead of this step, it skips to the partition table where it can't find any partitions.

So it goes straight from "Updates and software" to "Installation Type", but instead of being able to select wiping the disk and installing Ubuntu, it shows me an empty table with a drop-down that says "Device for boot loader installation". All the options related to the table (i.e. 'New Partition Table', 'Revert', '+', '-', 'Change') are greyed out or crash the installer when selected. When I choose 'Install Now' it tells me 'No root file system is defined. Please correct this from the partitioning menu'. 

I've used both Rufus and Unetbootin to configure the USB I'm booting from thinking that there could be an issue with either of the two programs and the newest Ubuntu distro. I also tried installing Ubuntu 18.04 thinking it was an issue with the 19.10, but I ran into the same issue with that installation. I've tried with both Secure Boot enabled and disabled. From what I've read it doesn't seem like enabling legacy boot would do anything. If anyone knows what wrong or anything that could help, please let me know. Also, let me know if you need more information. Thanks!

---

### Post by TheFu on 2019-11-13
Have you tried the "Try Ubuntu" option, then wiping the partition table completely using gparted BEFORE attempting any installation?
If that doesn't work, use gparted to make a few partitions with a GPT ...

---

### Post by CatKiller on 2019-11-14
> **lathorne said:**
> I want to overwrite Windows... it can't find any partitions.

Windows doesn't shutdown, it just suspends to mask its startup time. This leaves its partitions in a dirty state that the Ubuntu installer won't touch. 

You need to disable Windows' Fast Startup and shut it down properly.

---

### Post by oldfred on 2019-11-14
Dell typically needs UEFI update, SSD firmware update & RAID/Intel RST setting in UEFI for drives changed to AHCI.
If dual booting with Windows you do have to install AHCI drivers first.
You still have to fully shut Windows down, so it is not hibernated. Standard shutdown is with hibernation.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Many that erase Windows later want to reinstall it as they find one application or game that only works in Windows. Or later want to sell system and it needs Windows. Best to still do a full backup of Windows.

Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)

---

### Post by lathorne on 2019-11-14
Thanks everyone for your help! I got it working but disabling Fast Startup, updating the UEFI, and changing the RAID setting for drives to AHCI.

---

