---
title: "connecting the second sata drive - no boot"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by xmimagery on 2010-10-07
Ok, I've been trying to find a solution, I've looked everywhere but no luck. I have a 1TB drive, checked the cable & it's connected to motherboard SATA0. That motherboard is dual booting fine (windows7 + Ubuntu 10.04). 
 
My problem is when I connect the other SATA drive, SATA1. Upon restarting my machine, nothing happens & I dont see any boot menu (grub). 
 
I've checked the bios settings, boot drives are in order:
CD-ROM
SATA0
SATA1
 
To check if the second drive has physical errors, I've connected it as SATA0 (alone) & installed successfully windows & ubuntu 10.04. I formatted it & installed ubuntu studio. The drive is working fine. So I formatted it again, & now it's not connected.
 
How can I make it work? I want SATA0 to have both windws/ubuntu, & the SATA1 to be just a data storage drive.
 
please help

---

### Post by tommcd on 2010-10-07
> **xmimagery said:**
> 
How can I make it work? I want SATA0 to have both windws/ubuntu, & the SATA1 to be just a data storage drive.

Assuming you have the hard drives connected to the motherboard properly, and assuming you have successfully installed both Windows and Ubuntu onto the first hard drive and can boot both operating systems, then adding a second data drive should be a simple matter. See this:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

And welcome to the Ubuntu forums!

---

### Post by xmimagery on 2010-10-07
Thank you for your response, but forgive my lack of knowledge. If I connect the second hard drive, then the system will not boot into anything, just black screen. Bios settings are correct. Is there a way to boot directly into terminal so I can follow the setup mentioned in your link? or do I boot from ubuntu CD & run the terminal ?

---

### Post by tommcd on 2010-10-08
> **xmimagery said:**
> Thank you for your response, but forgive my lack of knowledge. If I connect the second hard drive, then the system will not boot into anything, just black screen. Bios settings are correct.
What is on the second hard drive now? Is it blank? Is it just data? Or does it have an operating system(s) on it.
> **xmimagery said:**
> 
 Is there a way to boot directly into terminal so I can follow the setup mentioned in your link? or do I boot from ubuntu CD & run the terminal ?
You should be able to add the second hard drive by booting to recovery mode. If there is no data on the second hard drive that you wish to keep, you could delete the partitions on the drive using GParted from the Ubuntu live CD. Or you could use **cfdisk** or **fdisk** from recovery mode if you can handle that.
I suppose if you have Ubuntu and grub on the second hard drive as well as the first, then that may be interfering some how. So just delete the OS partitions on the second hard drive. Then create the data partitions that you want there. You could do all of this from the Ubuntu live CD. Or use a Parted Magic live CD.
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by confused57 on 2010-10-08
You might also go back into the bios setup & see if the hard drive controller for sata1 is configured correctly. I had to go into bios on a Dell and set the 2nd HD controller to "Auto", the default was "Off",  the computer wouldn't boot with 2 drives connected and the 2nd HD controller was "Off"; likewise, with 1 drive connected, it wouldn't boot with the 2nd HD set to "Auto".  This was an IDE only system, don't know if it would apply to SATA?

---

### Post by xmimagery on 2010-10-08
thanks all.. will give it a go now.. will have an update in a while. appreciate your inputs..

---

### Post by xmimagery on 2010-10-08
THANK YOU all .. it worked .. I connected the second SATA, booted from CD, used Gparted to partition the new & format into NTFS, & labelled it as storage. For some reason, the label apparently has to be entered. When I left it blank, the system will not boot beyond the black screen. Grub wont start. Now everything is working fine. Thank you thank you thank you.

---

