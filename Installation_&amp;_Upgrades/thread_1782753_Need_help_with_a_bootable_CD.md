---
title: "Need help with a bootable CD"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by MyUsernameIsJoker on 2011-06-15
I downloaded windows 7,burned to the cd all the files from .iso,restarted,selected CD from the boot menu,and waited... But it wasn't loading windows 7 installer,it was loading ubuntu! What's the problem?

PS : The files I burned were already in bootable image,The disc I inserted was 100% new.

---

### Post by MyUsernameIsJoker on 2011-06-15
Here's what's in my CD :


Folders :


BOOT
EFI
SOURCES
SUPPORT
UPGRADE

Files :

Autorun.inf

BOOTMGR

MEDIAMETA.XML

SETUP.EXE

That's it,total 3.5 GB

PS : My windows cd broke,Luckily I still have the code on my desktop.

---

### Post by garvinrick4 on 2011-06-15
Ubuntu is on your HDD now?
If CD was first in boot order and it did not boot off of the CD then it is not bootable.
Make sure you are booting off of CD first in line.
Windows 7 is about 12 gig total so you downloaded the .iso for recovery disk most likely I
do not know how big the file is for recovery disk.
Do you have a CD with linux on it to boot from to check if you are booting from CD first?
Just going to have to take one step at a time until you figure out what the problem is.

---

### Post by travlemon on 2011-06-15
> **MyUsernameIsJoker said:**
> I downloaded windows 7,burned to the cd all the files from .iso,restarted,selected CD from the boot menu,and waited... But it wasn't loading windows 7 installer,it was loading ubuntu! What's the problem?

PS : The files I burned were already in bootable image,The disc I inserted was 100% new.

I know this probably isn't much help, but this link is to a tutorial on how to make a Windows 7 bootable usb flash drive.  I used it a while ago and it worked flawlessly for me. The problem is, you need to perform these steps from within a Windows installation:

[http://www.legitreviews.com/article/1031/4/](http://www.legitreviews.com/article/1031/4/)

That would work if you have a Windows XP, Vista, or 7 virtual machine set up.

Also, if you have an ISO image of the Windows 7 disc, you might be able to try the command in Linux, with your flash drive plugged in:

```
sudo dd if=/folder/where/the-iso-file-is.iso of=/dev/your-flash-drive
```

I believe this will erase everything else on the flash drive, and make a byte for byte copy of the ISO to the flash drive.  After that, you may just need to go into gparted and flag the partition on the flash drive as bootable.

Be very careful with this, and make sure you are specifying the right device.  For example, my flash drive on my computer is /dev/sdb1.  SDB is the drive, the 1 specifies the first (or only) partition.  The easiest way to find out what this ID is for your drive is to open gparted and select the flash drive from the drop down menu (you should know by the number of GB specified) and then look at the partition.  It will tell you /dev/sdb1 (or whatever yours is) right on the partition of the flash drive.

Hope this helps

---

