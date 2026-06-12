---
title: "moving ubuntu installation from drive"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by zero7404 on 2008-10-13
i have ubuntu installed on an external hdd so that when i start my computer and it's plugged in, grub loads ubuntu directly.

i'd like to take the ext3 and swap partitions and move them to my raid 0 drive and set up dual-boot with vista.

how would i go about doing this ? i'd have to make changes to the mbr on my raid 0 array, and then remove the mbr from the external hdd...

help and tips on how to do this welcome.

as i'm set up now, if i do a disk analysis on my computer when in ubuntu, it sees the raid 0 array as 2 seperate devices (it does not see raid in other words).

---

### Post by zero7404 on 2008-10-13
bump

---

### Post by zero7404 on 2008-10-14
here is some more information, hopefully someone can post some info on how i can go about doing this. I read the Fakeraid Howto, but i'm looking for verification on what i should/should not do in order to be successful.

on my external hdd, gparted shows the following partition info:

/dev/sdc1 (ext3, mountpoint /)
/dev/sdc2 (linux-swap)
/dev/sdc3 (ntfs, mountpoint /media/Mobile)

the 3rd partition is my shared partition i use between both vista and ubuntu.

i installed dmraid, and after running it, it recognized my raid 0 array correctly. gparted gave me the following info on my raid 0 array:

/dev/mapper/isw_ecfcjijjgh_RAID01 (ntfs)

of note for this raid array, there was an warning icon on the partition, when i go to info on it, the warning says that it's unable to read the contents of the filesystem.

if anyone needs me to post more info, please let me know so i can get it on this thread and try to proceed with moving my already existing /dev/sdc1 and /dev/sdc2 partitions onto the array, make the necessary changes to bootloader and ubuntu, and finally stop using the external hdd as an ubuntu startup.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-11-08
I am going to make an attempt to some thing similar
i have and existing ubuntu install and would like to move it to a raid0 setup
but what i don't under stand is how to get ubuntu to boot from a raid0 partition with out installing from the alt cd
witch i do not wanna do considering my install is fine

and zero7404 as soon as i figure this out i will tell you how to do what you wanna kuss its the same thing
sort of
if you have fake raid instead of software raid it will be a little different but ...

edit over 8 hours latter i am so close to getting this to work i can taste it

---

