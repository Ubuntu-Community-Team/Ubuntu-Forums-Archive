---
title: "Can't see internal HDD to create dual boot"
date: 2022-01-21
forum: Installation &amp; Upgrades
---

### Post by guy14 on 2022-01-21
Friend dropped off a Dell Desktop with WIN10.   After booting Linux using a usb iso I don't see the internal HDD.   When I didn't see the HDD in the File MGR I tried gparted & sudo blkid in  terminal.  Nothing shows the internal drive.

Do I need to something within WIN10 to expose the drive to Linux?

---

### Post by yancek on 2022-01-21
It may be that windows is hibrtnated and Linux systems will not mount hibernated partitions and therefore wil not be accessible from Linux.  Go to power settings in windows and turn off hibnation.l

---

### Post by guy14 on 2022-01-21
I think I may know what's happening but not how to cure it.  Every time WIN10 starts it tries to do an update, it gets to 56% and fails and states it is reverting the changes.  I'm guessing that it is somehow protecting the drive so it can try doing the update and the next reboot.

---

### Post by guy14 on 2022-01-21
I tried pausing the update process using Windows troubleshooter but WIN10 stated pausing isn't permitted.  So I am re-downloading all WIN10 updates and hope they can be installed correctly and then maybe the HDD will be visible to the Linux install process.

---

### Post by tea for one on 2022-01-21
> **guy14 said:**
> I tried pausing the update process using Windows troubleshooter but WIN10 stated pausing isn't permitted.  So I am re-downloading all WIN10 updates and hope they can be installed correctly and then maybe the HDD will be visible to the Linux install process.

Windows 10 updates often turn on hibernation without user intervention.
When the updates are complete, double check the hibernation as mentioned by [COLOR="#0000FF"]yancek[/COLOR] in post 2.

---

### Post by guy14 on 2022-01-21
I tried pausing the update process using Windows troubleshooter but WIN10 stated pausing isn't permitted.  So I am re-downloading all WIN10 updates and hope they can be installed correctly and then maybe the HDD will be visible to the Linux install process.

---

### Post by oldfred on 2022-01-21
Dell typically uses RAID for drives and you need to add AHCI drivers to Windows & then change UEFI settings to AHCI.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 

What model Dell?
What video?
Do you have latest UEFI firmare & if SSD latest firmware for SSD?

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

General UEFI info in link below in my signature.

---

### Post by guy14 on 2022-01-21
I tried pausing the update process using Windows troubleshooter but WIN10 stated pausing isn't permitted.  So I am re-downloading all WIN10 updates and hope they can be installed correctly and then maybe the HDD will be visible to the Linux install process.

---

