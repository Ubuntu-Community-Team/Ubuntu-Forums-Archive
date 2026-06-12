---
title: "Unable to install Ubuntu 14.04"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by arun.manuel14 on 2014-05-18
Hello,

I'm trying to install Ubuntu 14.04 LTS(amd64) on my HP laptop.
I created a bootable USB pen drive to boot into Ubuntu.
It successfully boots into Ubuntu , where I get the option to either try a live version or install.
Live versions works fine , when I try to install , i go through the normal procedure(FYI I'm trying to install Ubuntu along side Windows 7 home )
once i select install alongside windows it reboots and comes back to the option of try live version or install .

No errors to report , it just reboots back every time.

Can anyone please help me out!
Thanks!

---

### Post by squakie on 2014-05-18
Does it go all the way through the installation process?  At the end of an install you are notified that the system needs to restart and to remove the dvd from the drive.  What this is really saying is remove the install media - be it dvd or usb.  If your install completed, and you left the usb flash drive plugged in, it would just reboot from the flash drive.  If it completed, power down, remove the usb flash drive, then power back up.

---

### Post by Mark Phelps on 2014-05-18
> once i select install alongside windows it reboots and comes back to the option of try live version or install .


Most likely because your HP laptop already has the maximum of four partitions on the hard drive -- a common practice with HP.

To see, boot using the LiveUSB, when you get to the desktop, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions and filesystems on the drive.

---

### Post by SuperFreak on 2014-05-18
The method I used on my HP Pavillion  DV is shown in this link post #12 [http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions]("http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions")

---

### Post by Mark Phelps on 2014-05-18
> once i select install alongside windows it reboots and comes back to the option of try live version or install .


Most likely because your HP laptop already has the maximum of four partitions on the hard drive -- a common practice with HP.

To see, boot using the LiveUSB, when you get to the desktop, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions and filesystems on the drive.

---

### Post by arun.manuel14 on 2014-05-18
> **squakie said:**
> Does it go all the way through the installation process?  At the end of an install you are notified that the system needs to restart and to remove the dvd from the drive.  What this is really saying is remove the install media - be it dvd or usb.  If your install completed, and you left the usb flash drive plugged in, it would just reboot from the flash drive.  If it completed, power down, remove the usb flash drive, then power back up.


It doesn't go all the way through the installation process , infact i think the installation process doesn't even start for real . 
I just click on install alongside windows and system reboots back , thats all , and i start over .

---

### Post by arun.manuel14 on 2014-05-18
> **SuperFreak said:**
> The method I used on my HP Pavillion  DV is shown in this link post #12 [http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions](http://ubuntuforums.org/showthread.php?t=2191419&highlight=primary+partitions)


Thanks , I'll look through it and give it a shot and report back.

---

### Post by arun.manuel14 on 2014-05-18
> **Mark Phelps said:**
> Most likely because your HP laptop already has the maximum of four partitions on the hard drive -- a common practice with HP.

To see, boot using the LiveUSB, when you get to the desktop, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions and filesystems on the drive.


Yeah my disk does have 4 partitions , although it didn't come like that from HP , it had two partitions initially C and the recovery , I split the C drive to get two more partitions .

---

