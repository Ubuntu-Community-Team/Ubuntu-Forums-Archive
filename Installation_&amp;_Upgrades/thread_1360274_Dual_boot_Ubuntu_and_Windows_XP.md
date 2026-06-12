---
title: "Dual boot Ubuntu and Windows XP"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by mrob12 on 2009-12-20
I have Windows XP Pro installed on the following system: 100 GB Maxtor HD (c:\) which boots XP and a 80 GB WD (d:\) that I use to back-up.  Can I use a ver. 8.04 Ubuntu CD to install on the d:\ drive to dual boot with XP on the c:\ drive?  I would like to keep a small partition on the d:\ drive for backup.

---

### Post by darkod on 2009-12-20
Yes, you can. You can also try using more recent version than 8.04, up to you.
I would move all data from the 80GB disk and then delete all partitions. Then create first the data partition you want, it will probably be ntfs, you can create that from XP. Leave the rest of the disk as unallocated, DO NOT create ntfs partition for ubuntu.
After that, restart with the ubuntu cd in the cd drive, go into BIOS and set the 80GB disk as first choice in boot order (I'm talking about the hdd order, before your 100GB disk). Leave the cd-rom as device before the hdd. So that should boot you from the ubuntu cd, select Install Ubuntu, and in step 4 just tell it to use the Largest Available Free space on your 80GB disk.
Note: if the 100GB is selected as target by default, click temporarily on Erase and use whole disk, that will activate a drop down list under that option, select your 80GB disk and then select the choice Largest Available Free space.
Also note how your 80GB disk will be called in linux, probably /dev/sdb (the 100GB should be /dev/sda). In the last screen, before clicking Install, click on Advanced and double check that the bootloader (grub) will be installed on your 80GB disk (for example if it was called /dev/sdb in step 4, then the bootloader should go to /dev/sdb too).
That's it. :)

---

### Post by mrob12 on 2009-12-20
darkod, thanks for your response.  I just downloaded 9.10.  I will try the install tomorrow.

---

### Post by oygle on 2009-12-20
I have mine around the other way (primary is Ubuntu and secondary drive is XP); it works just fine with grub.  Here are the only mods I had to make (aprt from installing Ubuntu to the primary hdd) ..

menu.lst - add this at the bottom of the file

```

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP Pro
map             (hd0) (hd1)
map             (hd1) (hd0)
root            (hd1,0)
savedefault
makeactive
chainloader   +1

```

device.map - this swaps the files around when I select the XP grub prompt

```

(hd0)	/dev/sda
(hd1)	/dev/sdb

```

Of course, yours will all be around the other way, but no doubt you get the basics.

Oygle

---

