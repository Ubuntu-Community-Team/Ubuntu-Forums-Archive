---
title: "Installing Win7"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Troll_1988 on 2011-07-14
I have ubuntu 11.04 installed on my laptop. I wanna install windows 7 back on it, so i made a bootable CD and chose to boot from CD and when it goes to boot up it gives me and error. It says "Cannot boot from CD code 5". I went back to ubuntu and attempted to use wine and load the setup.exe off the CD but it just gives me and error, saying it cannot find a location to store temporary installation files. So it seems I'm kinda stuck, any help will be greatly appreciated.

---

### Post by daison3 on 2011-07-14
Well, If you installed the Ubuntu's first, then the then that i experience too is that you cannot install the windows 7 if you didn't override and delete the ubuntu 11.04, unless you have 2 partitions to your system that you can store the Windows7 and Ubuntu 11.04

**What is best for this situation:**
-First check your windows 7 DVD if there's a lot of scratchess to your DVD then you need to RE-Burn a Copy...or use a Mount USB if you know how to do that..
-Second override ubuntu to your system, and create a 2-Partitions to your system using the Windows 7 Installation Panel...
-Third, you need to install it first the Windows 7 to your Partition-1, then after you installed the windows 7, install ubuntu 11.04 to your partition-2.

**Might Be:**
The issue for that error, maybe a DVD error, try to use a USB Mounted, using your Startup Disc Creator to your ubuntu, go to System>Administration>Startup Disc Creator, and mount-burn yourUSB and your Windows 7.

---

### Post by daison3 on 2011-07-14
Well, If you installed the Ubuntu's first, then the then that i  experience too is that you cannot install the windows 7 if you didn't  override and delete the ubuntu 11.04, unless you have 2 partitions to  your system that you can store the Windows7 and Ubuntu 11.04

**What is best for this situation:**
-First check your windows 7 DVD if there's a lot of scratchess to your  DVD then you need to RE-Burn a Copy...or use a Mount USB if you know how  to do that..
-Second override ubuntu to your system, and create a 2-Partitions to your system using the Windows 7 Installation Panel...
-Third, you need to install it first the Windows 7 to your Partition-1,  then after you installed the windows 7, install ubuntu 11.04 to your  partition-2.

**Might Be:**
The issue for that error, maybe a DVD error, try to use a USB Mounted,  using your Startup Disc Creator to your ubuntu, go to  System>Administration>Startup Disc Creator, and mount-burn yourUSB  and your Windows 7.

---

### Post by mastablasta on 2011-07-15
if you have windows install CD  just insert it and format the disk and install windows on it.
 
format will erase all data.

---

### Post by Mark Phelps on 2011-07-15
You can't install Windows from Wine.

You have to boot from the MS DVD -- but it may complain if your drive is already filled with Linux partitions.  You may have to boot from an Ubuntu LiveCD and use the Gnome Partition Editor to remove the Linux partitions, first.

---

