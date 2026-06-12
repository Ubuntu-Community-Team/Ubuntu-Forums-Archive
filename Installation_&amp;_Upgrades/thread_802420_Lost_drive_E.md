---
title: "Lost drive E:"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by hcello on 2008-05-21
I downloaded and created an Ubuntu CD last week.  I then installed it on my SCSI harddrive. It booted fine and I used it for a day before realizing that I had several hundred photographs on that disk. I did not install Ubuntu inside of Windows XP but directly onto the harddrive. 
  When I boot up in XP I only have my 2 IDE drives(C&D)and missing E. So, I read the forum about uninstalling. I have a Windows XP home edition CD and tried to boot according to the thread to MS Dos. Unfortunately it did not see the drive.  I have a bootable diskette from Windows 98 with command.com, fdisk,and format etc.  So I booted with it and was able to remove the partition but when I tried to format I got a message saying wrong level of DOS. 
  Being a hardware guy I powered off and physically removed both the Tekram DC 390T scsi adapter and the IBM DNES harddrive. Then rebooted to ensure they were gone from the configuration. Then powered down, re-installed both the adapter and drive and then rebooted. The adapter was recognized but the drive still wasn't. 
  Is there a way to boot up with the Ubuntu CD and format the drive? If not what other options do I have?

---

### Post by Pumalite on 2008-05-21
You can use Gparted Live CD

---

### Post by hcello on 2008-05-21
What is Gparted CD?

---

### Post by Pumalite on 2008-05-21
It's a partitioner, but you can use it to check if it sees your partition.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Burn to disk and boot from it.

---

### Post by russo.mic on 2008-05-21
Well, it sounds to me like you've lost the partition because you installed ubuntu on to it.  The reason win xp can't see it is because it's formated ext3, which Windows can't read without the help of a driver.

Are you saying that you had photos on the drive you installed ubuntu on?  if so, almost certainly gone since to install you had to format the partition.  Uninstallation won't do any good at this point.  Here is the link to a driver that will allow you to see your e: ubuntu partition in windows at least, but it's going to show the / of ubuntu.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I know it says ext2, but it works for ext3 as well.  never had any problems with it.

You can't use the win98 cd to futz with the partition because 98 didn't support the NTFS filesystem, which XP uses by default. I'm confused as to your goals for the drive at this point.  are you trying to format to get ubuntu back on the drive?  or are you trying to reinstall xp on it, or just use it as a XP storage volume?

Russo

---

### Post by hcello on 2008-05-21
I know the photos are lost, but I do have Network Magic and I can get them from my laptop to put back on the desktop.  
I tried Ubuntu a couple of years ago. That version allowed me to come up in either Ubuntu or XP. I should have come up in XP and installed Ubuntu within XP. 
Anyway, all I want at this point is to have XP see the drive again.

---

### Post by Pumalite on 2008-05-21
Install this driver in XP:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by hcello on 2008-05-21
I installed this driver in XP:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
If I boot with the scsi drive powered off I can see drives C & D using fs-driver.  When I boot with the SCSI drive powered on I get a "device is not ready" pop up when I try to open IFS Drives. So I check system, hardware, device manager in XP and the drive is recognized there.

---

