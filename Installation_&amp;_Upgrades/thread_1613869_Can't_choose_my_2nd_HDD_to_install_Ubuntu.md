---
title: "Can't choose my 2nd HDD to install Ubuntu"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by mcapelati on 2010-11-04
Hi folks,


My computer has 2 HDDs:

> 1st = /dev/sda (320 GB) used for Windows 7 - recently installed
> 2nd = /dev/sdb (160 GB) will be used for Ubuntu 10,10 - trying to install


The problem is: the installer just refuses to show my second HDD, so, I can't install Ubuntu on it.


I try to boot using the regular installer AND the alternate installer (both i386 version), and the same problem happens...


I'm following the regular procedures: 

I boot with CD and select the right information: OK.

But when on that first screen "Allocate drive space", I choose "Specify partitions manually" (but if I choose "Erase and use the entire disk", it does not solve the problem as well...)

On the next screen, it only shows me information of my 1st HDD (with some confusing information along with strange partition names, like "/dev/mapper/pdc_eajaicdbhb1")



Note 1: my 2nd HD IS there, running. If I run GParted, it shows me both HDDs, with right partition information on them.

Note 2: I try to install an older Ubuntu version (8.10 AMD64), and, with this version, I could choose on what partition I'd like to install...



So, what is wrong ? :(


Thanks brothers !


Marcello Capelati

---

### Post by mcapelati on 2010-11-09
Please, guys, anybody could help me ??

(see attached image file)

I really would like to install and use the brand new Ubuntu 10.10.


Regards,
Marcello



> **mcapelati said:**
> Hi folks,


My computer has 2 HDDs:

> 1st = /dev/sda (320 GB) used for Windows 7 - recently installed
> 2nd = /dev/sdb (160 GB) will be used for Ubuntu 10,10 - trying to install


The problem is: the installer just refuses to show my second HDD, so, I can't install Ubuntu on it.

.
.
.



---

### Post by dabl on 2010-11-09
Is this a mix of an IDE drive and a SATA drive?

Regardless, the easiest solution is probably to pull the power cable off the drive that you DON'T mean to install on, and go ahead with the installation on the other drive.  It's easy enough to edit /etc/fstab to put the second drive back into the system, and if there's an OS on it that you need on the boot menu, OS prober will pick it up when you run "sudo update-grub".

---

### Post by mcapelati on 2010-11-09
Hi dabl,

No, they are both SATA drives.

I can do what you say. Even try to change that on BIOS setup. 

But I am afraid that, in doing so, after turning on the 1st HDD, that has Windows7 on it, what will happen with second HDD ? And with GRUB.

Seems that my problem has anything to do with new GRUB.

Because on older Ubuntus, like 8.10, on installation I could choose on what HDD I would install.

Thanks.


> **dabl said:**
> Is this a mix of an IDE drive and a SATA drive?

Regardless, the easiest solution is probably to pull the power cable off the drive that you DON'T mean to install on, and go ahead with the installation on the other drive.  It's easy enough to edit /etc/fstab to put the second drive back into the system, and if there's an OS on it that you need on the boot menu, OS prober will pick it up when you run "sudo update-grub".

---

### Post by Mark Phelps on 2010-11-09
Just do as already suggested above:
1) Disconnect the Win7 drive
2) Boot with only the other drive connected
3) Install Ubuntu to the connected drive

Then, reconnect the Win7 drive -- but -- continue to boot from the Ubuntu drive.  You may have to change the drive boot order in your BIOS setup because it will probably switch back to booting from the Win7 drive.

Once inside Ubuntu, open a terminal and enter "sudo update-grub".  This will generate a GRUB menu that will include an entry for Win7.

Next time you boot, you should get a menu with entries for both Ubuntu and Win7.

---

### Post by mcapelati on 2010-11-09
Allright. 

Thanks guys !


> **Mark Phelps said:**
> Just do as already suggested above:
1) Disconnect the Win7 drive
2) Boot with only the other drive connected
3) Install Ubuntu to the connected drive

Then, reconnect the Win7 drive -- but -- continue to boot from the Ubuntu drive.  You may have to change the drive boot order in your BIOS setup because it will probably switch back to booting from the Win7 drive.

Once inside Ubuntu, open a terminal and enter "sudo update-grub".  This will generate a GRUB menu that will include an entry for Win7.

Next time you boot, you should get a menu with entries for both Ubuntu and Win7.

---

### Post by oldfred on 2010-11-09
/dev/mapper indicated a RAID or LVM or other non-standard partition scheme. Gparted nor the installer will want to modify it as you have to use the RAID or LVM tools to edit those partitions.

If you are not running RAID:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by mcapelati on 2010-11-10
Hello oldfred,

Thank you SO MUCH: your information was very valuable, and help to, so I could fix my problem.

Just after running these 2 commands, the HDD /dev/sdb was shown, like magic, and I could install Ubuntu 10.10 on it !

Thanks again.

Regards,
Marcello



> **oldfred said:**
> /dev/mapper indicated a RAID or LVM or other non-standard partition scheme. Gparted nor the installer will want to modify it as you have to use the RAID or LVM tools to edit those partitions.

If you are not running RAID:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

