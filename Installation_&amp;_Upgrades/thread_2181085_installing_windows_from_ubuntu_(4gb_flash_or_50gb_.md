---
title: "installing windows from ubuntu (4gb flash or 50gb hdd partition)"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by ashtreylil on 2013-10-16
my hdd crashed a few weeks ago and ive been running ubuntu from my backup external hdd. after a week with ubuntu i just want windows back. i'm thankful that i can even use it due to ubuntu but i would prefer windows :/ so my guestion is how can i install windows from a flash drive or partition on my backup drive onto a new partition on the backup drive without erasing all of my backed up data. i've looked around and tried a few solution but none seemed to work. :(:confused:

---

### Post by Mark Phelps on 2013-10-16
How is your data "backed up"? Do you have an offline backup in the form of a USB stick/drive or an external drive? OR is the data still resident on the drive?

If the latter, you would need to shrink the partitions you have in place now to make room for Windows.  You can't do that while Ubuntu is running, so you would have to use a USB stick with Ubuntu or GParted on it to make the partition changes.

---

### Post by ashtreylil on 2013-10-16
> **Mark Phelps said:**
> How is your data "backed up"? Do you have an offline backup in the form of a USB stick/drive or an external drive? OR is the data still resident on the drive?

If the latter, you would need to shrink the partitions you have in place now to make room for Windows.  You can't do that while Ubuntu is running, so you would have to use a USB stick with Ubuntu or GParted on it to make the partition changes.

i have an offline storage (wd my passport) 
if i use Gpart to shrink the partition and change it to ntfs will it move all of the data out of the way instead of deleting it? i already have a live usb with ubuntu on it.

---

### Post by Mark Phelps on 2013-10-16
If you change the filesystem of an existing partition, you effectively "erase" everything current in it.  

You can't change a mounted partition while it's in use, so if you're trying to change the partition that Ubuntu currently uses, you can't work on that while Ubuntu is running.

If you only want Windows on the PC, then you can remove the existing partitions from an Ubuntu installer on a USB stick.

Once you have removed the existing partitions, when you reboot using the Windows install media, it will do the partitioning for you.

---

### Post by ashtreylil on 2013-10-16
> **Mark Phelps said:**
> If you change the filesystem of an existing partition, you effectively "erase" everything current in it.  

You can't change a mounted partition while it's in use, so if you're trying to change the partition that Ubuntu currently uses, you can't work on that while Ubuntu is running.

If you only want Windows on the PC, then you can remove the existing partitions from an Ubuntu installer on a USB stick.

Once you have removed the existing partitions, when you reboot using the Windows install media, it will do the partitioning for you.

im editing the partition my backup data is on and the drive is unmounted. im scared to accidentally erase my backup. i only have the 5 disc set of cdroms that i got with the purchase of the pc from geek squad (ugh i know they are more salesemen than real computer techs). anyway they didnt even label the dics with anything but "1 of 5, 2 of 5....ect." so i have no idea which one is the instalation media and i cant boot into the install from any of them. one of them is the windows recovery enviroment but seeing as how i have a dead hdd in my laptop it cant recover or install to factory settings. so i downloaded an iso that i got from sevenforums that is trusted and now i need to figure out how to install windows. im on ubuntu now so im not exactly sure what the process of making a bootable flash drive for instalation media is. i tried winusb on a flash drive and it didnt seem to work. so how can i make a flash drive to install windows on ubuntu? (i think it needs to have a mbr portion on it as well but am not completely sure)

---

### Post by Mark Phelps on 2013-10-17
You basically can't install Windows from Ubuntu; instead, you have to boot to the flash drive and install from that.

The best tool for doing this for Windows is the MS-provided DVD/USB creation tool.  For more info on this, you should visit the Win7 forums -- especially since installing Win7 is what you appear to want to do.  They have tutorials that will help.  But, you will need a working Windows PC to do this.

---

### Post by ashtreylil on 2013-10-17
> **Mark Phelps said:**
> You basically can't install Windows from Ubuntu; instead, you have to boot to the flash drive and install from that.

The best tool for doing this for Windows is the MS-provided DVD/USB creation tool.  For more info on this, you should visit the Win7 forums -- especially since installing Win7 is what you appear to want to do.  They have tutorials that will help.  But, you will need a working Windows PC to do this.

aww well i dont have another pc thats running windows :/ i guess my best bet may be to try to ask around here for help with some software until i can get near a windows machine.

---

