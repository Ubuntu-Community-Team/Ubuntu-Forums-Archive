---
title: "UBUNTU installation on winxp homw system"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by hydroparasite on 2008-01-15
**HI**

Hello guys i am a noobie to the world of linux but have using at my uni n all ! i would like to install ubuntu linux on my home pc but require some help so that i dont disturb my winxp home installation at all . i would also like to know what environment would be best suited for a student like me KDE or GNOME

my system config is : IBM 6792M

P4 2.4 GHZ, 20 GB HARD DRIVE, 256 RAM ,  NVIDIA 2 GEFORCE 

i was wondering what partition should i install ubuntu on , i got three partitions which are all in FAT32 system

C: winxp installed 9gb
E : 4.37gb
F:  4.41gb

i dunno how to go about the installtion , plz help me 

thnks

---

### Post by logos34 on 2008-01-15
unless you add some more ram, you probably should run Xubuntu or the like with a lightweight wm.  

At the very least you'll need to use the alternate Ubuntu cd to install (not enough ram for the gutsy live cd).  

Consolidate all your saved files on E: or F:, then install xubuntu on the empty one. (format ext3)

Take a look at this.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by wolfen69 on 2008-01-15
put in live cd.
select start or install.
when you get to the desktop, select install.
go through the setup routine and when you get to the part to partition, choose "manual".
next, you may want to join both 4gb partitions.
highlight each partition you want to delete, and hit "delete".
afterwards, you should have another 9gb partition that is unallocated.
choose "new" partition.
make a new swap partition first. make it 512mb or so. choose "swap" from the pull down menu. hit ok.
you will now have an unallocated partition left. highlight it.
choose "new" partition.
make mount point "/" (without quotes) and make file system ext3. ok.
check off the format box of the partition you've created. make sure it's not your fat32 partition.
click forward to continue installing.
good luck and have fun.

remember, we are here for any and all questions. i hope i was clear.

edit: as logos stated, xubuntu might be a better choice.

---

### Post by hydroparasite on 2008-01-15
**thnks logos for the reply appreciated ! so this means i cant install a regular GUTSY ubuntu distribution on ma pc ! what are the limitations in xubuntu ! **

---

### Post by hydroparasite on 2008-01-15
> **wolfen69 said:**
> put in live cd.
select start or install.
when you get to the desktop, select install.
go through the setup routine and when you get to the part to partition, choose "manual".
next, you may want to join both 4gb partitions.
highlight each partition you want to delete, and hit "delete".
afterwards, you should have another 9gb partition that is unallocated.
choose "new" partition.
make a new swap partition first. make it 512mb or so. choose "swap" from the pull down menu. hit ok.
you will now have an unallocated partition left. highlight it.
choose "new" partition.
make mount point "/" (without quotes) and make file system ext3. ok.
check off the format box of the partition you've created. make sure it's not your fat32 partition.
click forward to continue installing.
good luck and have fun.

remember, we are here for any and all questions. i hope i was clear.

edit: as logos stated, xubuntu might be a better choice.




thankz bro for the help ! appreciated !

---

### Post by hydroparasite on 2008-01-15
> **wolfen69 said:**
> put in live cd.
select start or install.
when you get to the desktop, select install.
go through the setup routine and when you get to the part to partition, choose "manual".
next, you may want to join both 4gb partitions.
highlight each partition you want to delete, and hit "delete".
afterwards, you should have another 9gb partition that is unallocated.
choose "new" partition.
make a new swap partition first. make it 512mb or so. choose "swap" from the pull down menu. hit ok.
you will now have an unallocated partition left. highlight it.
choose "new" partition.
make mount point "/" (without quotes) and make file system ext3. ok.
check off the format box of the partition you've created. make sure it's not your **fat32 partition.**
click forward to continue installing.
good luck and have fun.

remember, we are here for any and all questions. i hope i was clear.

edit: as logos stated, xubuntu might be a better choice.

ALL my partitions are in FAT32. Do you mean the one with XP installed coz the new partition will now have a ext3 file system .

---

### Post by wolfen69 on 2008-01-15
the non-xp partition will become ext3. xp will remain fat32.

---

### Post by neratokio on 2008-01-15
Ubuntu and xubuntu, whats the differentce ?

---

