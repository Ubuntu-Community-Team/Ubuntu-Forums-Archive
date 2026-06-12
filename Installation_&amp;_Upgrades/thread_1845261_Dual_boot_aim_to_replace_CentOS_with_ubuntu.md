---
title: "Dual boot: aim to replace CentOS with ubuntu"
date: 2011-09-16
forum: Installation &amp; Upgrades
---

### Post by Ubu_user_101 on 2011-09-16
I currently have a dual boot PC (half Xp and half CentOS5). They are different partitions on the same physical disk.
 
My boot loader is GRUB.
 
I wish to replace CentOS with Ubuntu but I have a few questions to try and prempt any problems.
 
Do I need to remove GRUB and replace it with a debian bootloader such as lilo?
 
Or 
 
Can I simply reformat the linux partition and install ubuntu in the clean disk space?
 
In fact, do I actually need to reformat the partition (type 8E) at all, or can I simply install Ubuntu on the space CentOS currently populates?
 
My first post on here, any help appreciated
 
Thanks
J

---

### Post by Frogs Hair on 2011-09-16
Hello and Welcome 

You can refomat the Linux portion and install Ubuntu but you will need to update Grub when Ubuntu is installed to get both operating systems booting .

I remove Ubuntu using Windows disk management the night before the new releases and install the new version in the same space .

---

### Post by ajgreeny on 2011-09-16
If you choose "Something else" (manual partitioning) at the partitioning stage of the installation of 11.-04, and assuming the name has not been changed again if you want to try 11.10, you can then delete the CentOS partitions and replace with ubuntu.  There is no need to delete the partitions first, though you can do so if you want to.

If grub was on the root of sda when you installed CentOS, Ubuntu will overwrite it with grub2 when installed and you will not need to do anything else;  it will find and add WinXP to the grub menu as well with no work for you; all done automatically.

---

### Post by Blasphemist on 2011-09-16
It is during the allocate disk space step of the installation that you should choose "something else" to manually choose the partition. If Centos is in a logical partition within an extended partition, you can just choose that partition and edit, set it's mount point as /, check the box to format the partition and set it to EXT4 journaling file system. And then when asked, install the bootloader which will be grub2 to the mbr of the appropriate drive, sda for the first hard drive.

---

### Post by garvinrick4 on 2011-09-16
You are used to grub legacy most likely with a menu.lst, grub2 is a bit different and a lot
nicer. So do not look for the menu.lst
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 
Enjoy your UBuntu. Welcome to the Ubuntu Forums.

In my signature under main page you will see a post installation manual for all releases of Ubuntu.
Nice to have when used to "yum" a bit different in the apt-get's

---

### Post by Hakunka-Matata on 2011-09-16
> **ajgreeny said:**
> If you choose "Something else" (manual partitioning) at the partitioning stage of the installation of 11.-04, and assuming the name has not been changed again if you [COLOR=Red]want to try 11.10[/COLOR], you can then delete the CentOS partitions and replace with ubuntu.  There is no need to delete the partitions first, though you can do so if you want to.

If grub was on the root of sda when you installed CentOS, Ubuntu will overwrite it with grub2 when installed and you will not need to do anything else;  it will find and add WinXP to the grub menu as well with no work for you; all done automatically.

FWIW, 11.10 beta is working well for me, just today a gaggle of updates have apparently fixed a recurring 'system problem popup'.  I've been using 11.10 for maybe 10 days, constant improvement.

---

### Post by Ubu_user_101 on 2011-09-19
Thanks for all the replies.
 
Once a read a bit further into the Ubuntu install and intro pages it talks about boot loaders etc.
 
Having backed up my Xp files and as there was nothing on CentOS worth keeping i set about installing Ubuntu.
 
This was very simple. I deleted the CentOS partition, reformatted and installed ubuntu in its place. 
 
After removing the install disc it booted fine.
 
happy days
 
Cheers
John

---

