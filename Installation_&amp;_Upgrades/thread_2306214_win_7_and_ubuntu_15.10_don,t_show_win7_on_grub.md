---
title: "win 7 and ubuntu 15.10 don,t show win7 on grub"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by coldfear2 on 2015-12-13
I have win 7 x64 then i install ubunto then grub just shows with left shift and win7 dont is visible in grub menu, then i repair win 7 with bootrec /fixmbr and reinstall ubunto ... Same problem !!!

I have 2 disks , last one just for win backups and first with 2 win partitions and 2 linux, ext4 and swap.

Maybe my bootrec /fixboot with bootrec /fixmbr works for grub show me win 7 ????

---

### Post by yancek on 2015-12-13
When you run the windows boot repair command, it will just show windows.  In order to show a Linux system in the windows bootloader, you will need to manually create and edit the boot files in windows or use third party software.  Without more information, not much to suggest so I would suggest that you get the boot repair software from the link below, download and create a bootable CD and then boot it.  There is an option to Create BootInfo Summary which you should select and then paste a link to it here.  Do not try to make any repairs.  If windows didn't show up orignially, you might have tried to run:  sudo update-grub.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by coldfear2 on 2015-12-13
My wifi network seems fine but when i type password and choose connect the ubuntu just dont connect. Downloads from ubuntu Linux are out of question...

I have a driver of the equipment just for Linux but i just can't acess the folder because there is some problem with the archive system, i type just the right name and the ubuntu says that "is no such directory".

How i do to access the previous folder in terminal ??? cd\ in Windows ou just cd.. ???

I really have to get boot-repair, i have a free CD-RW i'll try it !!!!

---

### Post by coldfear2 on 2015-12-13
Boot-repair-tools repeared my problem !!! doing just nothing , great tools and thks for support !

now has configuring my TP-LINK i have driveres and i know that i'd do a make compiling the driver.... ?!!??

---

