---
title: "HardDrives not seen in Ubiquity but can be see in parted"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by Diar16335502 on 2014-09-11
Hi,

So as the title says, I am trying to install but ubiquity is not showing me any devices, but I can see two hard drives in :-

fdisk
parted
KDE Partition Manager
Partition Manager

So confused why everything can see the disks but the install application. I tried putting ubiquity in debug mode but this didn't seem to have any affect. Is this a common problem ? Does any one know of a fix/work around ?

Thanks,

Richie.

---

### Post by yancek on 2014-09-11
I don't know if this is a bug in the installer but it is certainly common as anyone reading through posts on this forum would see.  If you are familiar with Linux drive/partition naming conventions, use GParted to determine which partitions on which drive you have windows or any data partition you do not want to overwrite.  Actually, since you haven't indicated if you have windows you would need to post that info, if you do which version.  If you have any other operating system, same thing.  Did you see this after selecting the manual "Something Else" installation method?  You could post this info from the installation medium from a terminal type:  parted -l(Lower Case Letter L in the command)

---

### Post by Diar16335502 on 2014-09-11
Hi,

These are new paritions I have not used windows in at least 3 years. I used fdisk and placed a /boot partion on but this made no difference. Ubiquity entries in the syslog show it using "os-prober" to pole every device under /dev/mapper. It then complains the Raid device is not found. If i disable the RAID controller it says it can't find the correct number of devices in the Array even though there is no array.

---

### Post by yancek on 2014-09-11
Things look different when you are using RAID.  I don't use it so can't make any suggestions.  You might post the output of parted -l or fdisk and someone might have a suggestion.

---

