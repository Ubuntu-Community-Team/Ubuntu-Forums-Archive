---
title: "clean install"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Brizlitman on 2012-03-25
i really want to clean install oneiric. This is probably a silly newbie question but i have the system recovery partition toshiba created and the  100 mb partition. Would the clean install be detrimental because of the presence of those partitions? I doubt it but i want to be sure

---

### Post by collisionystm on 2012-03-25
> **Brizlitman said:**
> i really want to clean install oneiric. This is probably a silly newbie question but i have the system recovery partition toshiba created and the  100 mb partition. Would the clean install be detrimental because of the presence of those partitions? I doubt it but i want to be sure


The system recovery partition from Toshiba is most likely Windows 7. You can factory re-install Win7 any time with this.

You can do a clean install, you just need to decide if you want to keep the restore partition or not. If you want it, just leave it. You can select Win7 Loader from GRUB to start a factory install of Win 7 if you ever choose to do so.

---

### Post by sammiev on 2012-03-25
I would suggest you have a copy to CD/DVD or USB of your system recovery partition before you do anything. Most people will do this out of the box when the unit is new. Then you can do anything without any worries. :)

---

### Post by garvinrick4 on 2012-03-25
Install gparted if you do not have it installed:
```
sudo apt-get install gparted
```
Now take a screenshot of gparted and use paperclip icon on top (attachments) and upload to give us a look at your partition scheme on gparted. Will be able to make sure we tell
you the right sda# to install fresh so as to be no problems.

---

### Post by Sylslay on 2012-03-25
Don't tuch that 100MB, OS.

Download:

[http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

or :

[http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

burn live CD,

Resize Main Windows partiton (make free space for Linux).

Thane run Ubuntu live cd , start installer 
and if number of total primary partition is alreardy more then 2,
 (C partiton + D partiton plus Recovery 100MB) then

crete logic pratiton for ext4 and logic partion for swap space (2 grater then amount or RAM)

PS. Do a backaup if You don't have any Windows Recovery CD!!!!

---

### Post by Mark Phelps on 2012-03-26
> **Sylslay said:**
> ... Resize Main Windows partiton (make free space for Linux).

NOT a good idea with Win7.  While this MIGHT work OK, it also might end up corrupting the Win7 OS filesystem and rendering it unbootable.  High price to pay for using the wrong tool.

If you insist on shrinking Win7, use its Disk Management utility to do that.  Much more primitive than GParted, but it won't corrupt the filesystem and will leave Win7 in a bootable state when done.

---

### Post by collisionystm on 2012-03-26
Since when did dual boots become so complicated?

I have never had a problem doing a dual boot with just the tools that are presented during install. It has to be at least 20 times now.

Sounds to me like a bunch of hear-say.

---

