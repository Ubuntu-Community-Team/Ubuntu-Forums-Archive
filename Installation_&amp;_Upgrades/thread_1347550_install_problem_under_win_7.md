---
title: "install problem under win 7"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by vlad-i on 2009-12-06
hi , 

When i try to install from win7 it goes well until the restart is needed or the action second to copying the files to my hdd, i have chosen to install in windows, and the error i get is that it does not have the permission to .... although i have run it as administrator.

 tried to search the forum for something similar and did not find it , if there is sorry for re-post. 

 The second thing i did is to run it wit boot from cd and all went well until i had to chose the partition to install to, it kept saying "no primary partition defined"  or that it did not find any systems .. 

 help ?! 

thank you very much

---

### Post by darkod on 2009-12-06
Do you have only one hdd?
If you are not running RAID try booting with the ubuntu cd, select Try Ubuntu option and that should open up the desktop. It will be running from the cd. Open terminal (Applications-Accessories) and execute:
sudo apt-get remove dmraid

Then reboot and you can try booting with the cd again and Install option, or you can decide to install from within win7 if it works this time. Your choice, but read around about the differences between ubuntu dual boot side-by-side install and wubi install (inside windows) because it's not the same.

---

### Post by vlad-i on 2009-12-06
i saw that it's not the same, and after some time i decided to install separate from my windows 7 , so i just want to do a fresh install on a partition i have already created  i have 3 hdd's and no raid (i save my files on blue-rays). 

 Will try the method you mentioned , thank you for you extremely fast reply .

---

### Post by darkod on 2009-12-06
With multiple drives make sure grub2 is installed where you want it to be and that you set that drive to be first in boot order in BIOS.

---

### Post by vlad-i on 2009-12-06
the first hdd in bios boot is the one with win7 , so i presume i will have some issues there also considering that the one i want to install ubuntu 9.10 is the third on the list .

Question: If i free 50 gb on the second partition of the first drive (on the first drive i have 2 partitions one 50 gb for win7 and a second of 350gb) will i be ambe to install on the second partition ? and all will bee ok ?

---

### Post by darkod on 2009-12-06
No issues at all. Just remember to put drive3 first in BIOS list BEFORE booting with the cd and installing ubuntu. It can work if you switch it later usually, but it's better to be made first in boot order before ubuntu and grub2 are installed.
In the final step of the install, before clicking Install button, click on Advanced and check if grub2 will be installed on that drive. Remember the name from the step 4 where it asks where to install. If it's drive3 called /dev/sdc for example, in Advanced option in the final step also grub2 should say that it will be installed on /dev/sdc.

---

### Post by vlad-i on 2009-12-06
i am at step 5 now and it still doesn't let me choose the second partition of my first hdd, from the looks of it it doesn't recognize my partitions and it shows me the whole drive but not the individual ones free space and occupied space (i did the remove dmraid from earlier and restarted) 

 i only have the choice of "use as"  "format " "mount point" 

 how can i make it so it will select my second partition of the first drive ?

p.s: when i try to continue after selecting partition 2 it says " no root file system is defined"

---

### Post by darkod on 2009-12-06
If you created the partition from windows it can't create linux filesystem. Select the partition you planned for / (root), at the bottom click Change button. Change Use as into Ext4 filesystem, tickthe format box, and select mount point /.
Do the same for the partition you planned for swap, if you created such.

If not, you need to delete the partition you planned for ubuntu if it's only one, because you need at least 2, / and swap. A third partition, /home, is not necessary but it's a good option because it will hold your documents and settings if the ever reinstall another version over /.

There was no need to create partition in advance, especially from windows. It can't be done. You only needed to make sure you have empty unpartitioned (unallocated) space to create partition into during the install process.

---

### Post by vlad-i on 2009-12-06
so basically i need a drive only for it made into three partitions one for /  another for /swap and another for /home .

how safe is the option to choose the biggest amount of free space and go from there , i have choose that and it shows that it will create 2 new partitions and so on , but it also says that it will format sdc .. i am inclined to g with this options since it will automatically find space there and it's a lot but i don;t want any of my files to be deleted or any hdd formatted that i have now.

---

### Post by darkod on 2009-12-06
> **vlad-i said:**
> so basically i need a drive only for it made into three partitions one for /  another for /swap and another for /home .

Yes and no, or enough unallocated space on existing drive to create those partitions in the unallocated space. It doesn't need a drive of its own.
If it's an NTFS partition which is only half full, it won't work. It needs to be unallocated unpartitioned space. A partition is considered unavailable space unless you delete it. The partitioner allows you to delete existing partitions and that will create unallocated space but be careful what partition you delete and whether you need the data on it. All data will destroyed on it.

---

### Post by oldfred on 2009-12-06
It may be too late but if you have multiple drives, I like to have an operating system on different drives with the boot for that system in the MBR of that drive. Since grub/ubuntu is the most flexible I make it the first boot drive and it finds windows without issue (ususally;)). The advantage is if you ever have a hard drive issue with the boot drive, you can switch drives in BIOS and still boot another operating system. I have 3 drives and 4 operating systems so I have different MBR setups for each drive.

---

### Post by vlad-i on 2009-12-06
ok, great , got it ...

"how safe is the option to choose the biggest amount of free space and go from there , i have choose that and it shows that it will create 2 new partitions and so on , but it also says that it will format sdc .. i am inclined to g with this options since it will automatically find space there and it's a lot but i don;t want any of my files to be deleted or any hdd formatted that i have now." 

is it more ok to use this at this time ?

---

### Post by darkod on 2009-12-06
Yes, that's fine too. But I am confused, because if you have unallocated free space to use that option, you would have no problem manually creating partitions yourself into that space. It's difficult like this not looking at the computer. :)
It will not create separate /home but that's not necessary anyway.

---

### Post by vlad-i on 2009-12-06
i know i have 70 gb free on a drive that does not have any partitions but it doesn't show it in the earlier screens , i am looking now at it (i am using try ubuntu bla bla now and writing from the virtual desktop it opens, have the installer by my side).  

If it doesn't show it but this option works it should be ok, so i would be inclined t go with this one , just that i don;t want my files to be deleted :D :))) it's silly i know but if it does not show the 50 gb free and the 70 gb on th other drive maybe it can confuse them and format a hdd that has important stuff on it.

---

### Post by darkod on 2009-12-06
Yes, it seems confusing why it's not showing them.
Go with that option, that's fine.

---

### Post by vlad-i on 2009-12-06
installing now with that option , will be back with the details after i have seen where exactly it has installed it and how the boot will be . thanks for your help and sorry for the "noobiesm" (if i can create words like that). 

 thanks again 
 V

p.s: after that will be code time for cs4/3ds max and all the rest of my programs . :))) that will be fun

---

### Post by vlad-i on 2009-12-06
the installation work out ok with that option, under win 7 i cannot even see the partitins and apparently not even the space that was taken from the hard drives. All is good and now i am moving forward with drivers issues and programs . 

 Thanks again 
 V :popcorn:

---

### Post by darkod on 2009-12-06
Yes, windows can't read linux partitions by default. Glad it worked out. Enjoy it now.

---

