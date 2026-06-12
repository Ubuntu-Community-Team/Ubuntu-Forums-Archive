---
title: "Safest and easiest way to uninstal ubuntu ?"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by rishi_singh on 2011-09-26
I want to remove ubuntu 10.04 and its partition as safely and easily as possible. Online articles say that improper methods can render a system useless. I am not an expert in computer science and linux, so i cant do this easily. Any suggestions to solve my problem ?
I will instal  ubuntu 11 later.

---

### Post by oldfred on 2011-09-26
The issue is the boot loader, not Ubuntu per se.

What system are you still going to boot? You should install its boot loader first then delete the Ubuntu partition. The grub2 boot loader in the MBR relies on the grub2 files in the Ubuntu partition, so if you delete the partition first, you will not be able to boot.

If another install of Linux just boot it and install its boot loader to the MBR. If Windows do a Windows repair that reinstalls the Windows boot loader to the MBR.

Always best to have liveCD of current version of all systems installed. Since most install Ubuntu from a liveCD that works for Ubuntu, but if Windows you need to make a repairCD/USB.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If you need more info, post details of what you have installed.

---

### Post by collisionystm on 2011-09-26
Did you dual boot with Win 7?

---

### Post by rishi_singh on 2011-09-26
> **oldfred said:**
> 
If you need more info, post details of what you have installed.

Sorry for not providing all the details. I have windows 7 and ubuntu 10.04 installed side by side. I am not seeing any wifi connections in ubuntu - no linux drivers for my card i guess. Also, i dont want my win 7 to be visible inside ubuntu. I want to solve these problems.
Therefore, i want to remove 10.04 and put 11. My problems might go after that.

Recovery cd - i did not get one, but i made one which spans 3-4 DVD's. Dont know which one to use to replace the win 7 mbr. 

Also, if i replace linux loader by win 7 loader from recovery disk, will the entire partition of linux be free to use ?

---

### Post by collisionystm on 2011-09-26
Okay. So first thing I would do is run an 11.04 live CD to see if your hardware is even recognized. That will answer that question.

Secondly, If you want to remove ubuntu and go back to windows you are going to need a Windows 7 install DVD handy to fix your MBR and re-expand your ntfs partition.

---

### Post by rishi_singh on 2011-09-26
> **collisionystm said:**
>  fix your MBR and re-expand your ntfs partition.
I had fixed the mbr for someone else in a similar situation before. But i dont know how to re expand my ntfs partition. How do i do that safely. My laptop has a lot of important work related stuff and i need to use it for studying too. So, i have to be very sure of what i am doing.

---

### Post by oldfred on 2011-09-26
Do not confuse the vendor recovery DVD set which is just an image of your hard drive as purchased with a Windows recovery CD which is for repairs. The Vendor DVDs will not normally run any Windows repairs.

With any system re-configuration, you need to have good backups. Unless you data is not valuable.

You should be able to use gparted from liveCD to remove Linux partitions, then use Windows MMC to modify Windows partition. But if reinstalling soon, do you not want to just leave space available for the time being?

Wifi often is an issue as there seem to be too many versions to auto install. You have to determine version and down load with an Ethernet connection first. You can mount your Windows partition(s) as read only or mount and set to not be available, otherwise you do see them.

---

### Post by collisionystm on 2011-09-26
> **rishi_singh said:**
> I had fixed the mbr for someone else in a similar situation before. But i dont know how to re expand my ntfs partition. How do i do that safely. My laptop has a lot of important work related stuff and i need to use it for studying too. So, i have to be very sure of what i am doing.

When you put in your Windows 7 dvd, you advance through the setup until you reach the drive partition section. It will show your existing windows installation and extra partitions, aka your ubuntu. You delete the ubuntu partitions, click on your windows partition and hit expand. Dont progress any further in the install, just reboot. 

I have done this several times. It works.

---

### Post by Mark Phelps on 2011-09-27
> **collisionystm said:**
> When you put in your Windows 7 dvd, you advance through the setup ...

Which would be fine ... except ... the OP does not have an Windows install DVD; instead, they said they made Restore DVDs -- and those are likely to only provide ONE function: overwrite the drive to reinstall Win7 from scratch.

---

### Post by rishi_singh on 2011-09-27
> **Mark Phelps said:**
> Which would be fine ... except ... the OP does not have an Windows install DVD; instead, they said they made Restore DVDs -- and those are likely to only provide ONE function: overwrite the drive to reinstall Win7 from scratch.

Yes. I guess i did something wrong. I replaced the mbr with win 7 loader using recovery disk. Inside win,i deleted ubuntu partition. Then, created it again. Now that 40 gb cant be merged with win os partition. It is usable though. However, i cant instal ubuntu 11.04 into it easily. I get some options that i dont understand. Please advise !

The post for that is here :
[http://ubuntuforums.org/showthread.php?t=1850735](http://ubuntuforums.org/showthread.php?t=1850735)

---

### Post by collisionystm on 2011-09-27
> **Mark Phelps said:**
> Which would be fine ... except ... the OP does not have an Windows install DVD; instead, they said they made Restore DVDs -- and those are likely to only provide ONE function: overwrite the drive to reinstall Win7 from scratch.

Depends on who made the computer. For instance, I have a DELL that came with a Win 7 restore disk. 

Generally the CD itself gives you 'normal' options. However when you restore from a partition on the computer, that is when you cannot choose.

---

### Post by rishi_singh on 2011-09-27
Never mind. Did it myself. Win 7 recovery disc - command prompt - bootrec /fixmbr - go to windows - prepare old partition - instal ubuntu 11.04 - use ext3 journalizing bull-poop - done.

What those steps mean, i dont understand. But it got the job done. A few more hours in linux and i can declare myself a phd in computer science. :) ... :( ... ):P

---

