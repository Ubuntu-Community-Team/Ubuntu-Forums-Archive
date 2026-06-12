---
title: "Trying To Move To Ubuntu..."
date: 2019-01-21
forum: Installation &amp; Upgrades
---

### Post by ninzombie2017 on 2019-01-21
[FONT=arial]I have an HP 15 - Intel Core i3-8130U - Intel UHD Graphics 620 - 1TB HDD - 16GB Intel Optane Memory, 16GB DDR4.  Windows 10 - bleh! Trying to install 18.10 *OR* 18.04 LTS

So I really want to make the leap over to Ubuntu, however, even using a good USB drive, and following the directions on how to download and create the bootable USB drive, this is what ocurred:  

1) At first the "live" version of Ubuntu would load like a charm but unable to see the hard disk to install to.  Thus, unable to install.
2) Though it might be a problem with the creation of the USB drive, so I low-leveled the USB drive, re-partitioned, reformatted, recreated the bootable USB drive, now getting a fatal error right off the bat - will not even go to the Ubuntu menu to choose live or install.

This is a pretty vanilla laptop...so I don't understand what could be causing this...

Any thoughts?[/FONT]

---

### Post by yancek on 2019-01-21
Some detailed information on dual booting Ubuntu with windows 10 at the Ubuntu site below.  One thing is to verify that fastboot and hibernation are off.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by CatKiller on 2019-01-21
> **yancek said:**
> One thing is to verify that fastboot and hibernation are off.
Yep, that sounds exactly the initial issue for the OP.

I wouldn't install 18.10. Stick to the LTS releases.

---

### Post by oldfred on 2019-01-21
If not Windows fast start up setting.
Many systems have drive set for RAID or Intel SRT even when only one drive.
Install the AHCI driver into Windows and then change UEFI setting to AHCI from RAID.

Have you updated HP's UEFI to latest version from HP.
You may have to redo settings in UEFI as it will change many back to defaults.

---

### Post by ninzombie2017 on 2019-01-27
Ok, ready to bang my head up against a wall.  After trying all of these suggestions - thank you to all of you by the way - I am still struggling.  I am going to go through where I am stuck, take pictues with my cell-phone, and post them here for you folks to look at...has to be an answer...

---

### Post by oldfred on 2019-01-27
Is drive an SSD, or NVMe SSD?
If so you may also need to update firmware on it..

       HP Envy 17 - 18.04.1 works See post #3
[https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797)

---

### Post by ninzombie2017 on 2019-01-30
YEAH!!!!! 18.04 LTS  on my HP!  Had to do a little tinkering to make it work with the WiFi drivers, but hellllloooo Ubuntu and GOODBYE WINDOWS 10!!

---

