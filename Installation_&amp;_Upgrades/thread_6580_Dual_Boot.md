---
title: "Dual Boot"
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by Infatuated_iPod on 2004-11-29
How do i make it so that i can run both Windows and Ubuntu on the same computer, SUse did it automatically, i am afraid to do it on this computer because i dont want to erase windows. ThankS!

---

### Post by Magneto on 2004-11-29
[QUOTE=Infatuated_iPod]How do i make it so that i can run both Windows and Ubuntu on the same computer, SUse did it automatically, i am afraid to do it on this computer because i dont want to erase windows. ThankS![/QUOTE]
 be aware of your partitions while installing- dont format your vfat or ntfs partitions
windows will be automatically setup in your grub boot menu during installation

---

### Post by Infatuated_iPod on 2004-11-29
Huh? Is it going to do it automatically, or do i have to do something?

---

### Post by Magneto on 2004-11-29
if you dont erase it, the ubuntu setup will do it automatically :)

---

### Post by Infatuated_iPod on 2004-11-29
So what do i do in the partition menu?.

---

### Post by Magneto on 2004-11-29
[QUOTE=Infatuated_iPod]So what do i do in the partition menu?.[/QUOTE]
 I dont know how youre trying to setup your system/how your system is setup so Im not sure- can you tell me a lil bit more :)  How many disks/partitions are you using ?

---

### Post by Infatuated_iPod on 2004-11-29
I am really new to doing things myself, i am used to having my hand held through every little thing on windows. I have an 80GB HD, and i would like to have 10 GB for ubuntu and leave the rest for XP.

---

### Post by Magneto on 2004-11-29
[QUOTE=Infatuated_iPod]I am really new to doing things myself, i am used to having my hand held through every little thing on windows. I have an 80GB HD, and i would like to have 10 GB for ubuntu and leave the rest for XP.[/QUOTE]
 what's on the disk now? is all 80gb in one huge partition?

---

### Post by Infatuated_iPod on 2004-11-29
yea i just got a new hard drive not to long ago, and installed windows on the whole thing...

---

### Post by Magneto on 2004-11-30
[QUOTE=Infatuated_iPod]yea i just got a new hard drive not to long ago, and installed windows on the whole thing...[/QUOTE]
 why dont you repartition it so you have linux on a completely separate part of your harddrive - using partition magic etc
it will help protect your data  
something like this
80gb disk
hda1 winxp -68gb
hda2 ubuntu -10gb
right now it seems you have one huge 80gb windows partition

---

### Post by herrard on 2004-11-30
not trying to make it more complicated but I suggest you make a special partition for the boot loader

hda1 winxp
hda2 /boot  <<< boot loader (grub or lilo)
hda3 /          <<< root

this will make it easier for you to uninstall linux if you ever decide to in the future... by default I think Ubuntu wants to install the boot loader in the MBR--I suggest you don't do this, instead install the boot loader in /boot partition or your root partition if you decide to not make a special partition for the boot loader (following Magneto's suggested partition scheme)

also, there is the "boot flag" option in ubuntu... make sure that you flag only one partition and that the partition you flag is the one with the boot loader installed.  Of course, where the boot flag is will be irrelevant if you decide to install the boot loader in the MBR (which I strongly suggest you don't because it can cause possible complicatons--nothing too serious but it will be quite annoying if you try to remove linux)

---

### Post by Infatuated_iPod on 2004-11-30
I thank you both for your help, but you have to understand i am a complete biginer at this and i dont know how to do that. Haha. What is partition magic? I tired to mess around with the partition options during the instillation but nothing happened. Since i was sure that i was going to mess up i just aborted the instillation. Is there anywhere where i can get like a step by step instruction on how to do this correctly? Thanks !

---

### Post by Magneto on 2004-11-30
okay- [www.google.com](www.google.com)
:)
partition magic is a windows program that will let you resize partitions on a harddrive without losing data.  If you can't afford to lose the data on your windows OS and can't copy it to another PC or CD then you will need something like this in order to use some of that free space on your hard drive for Ubuntu.

If you can manage being able to reinstall windows - do it- but when you install it change the size of your partition to leave 10gb of space, since that's how much you wanted to use for ubuntu. Then you can install Ubuntu, during the installation Ubuntu will automatically add windows to a menu you will see after turning on your computer.  
Please read about partitions partitioning a harddrive etc - google will have many sources of information it will help you to understand how your PC works and what you need to do in order to get Ubuntu and windows playing together
google dual boot linux and windows 
google harddrive partition

---

### Post by Infatuated_iPod on 2004-11-30
I am kind of upset at myslef. I have been using computers for years, and i JUST now realize the advantages of partitioning, thank you for opening up this whole new world for me.. HAHA. If i understand correctly, is it possible to have windows OS on one partition, linux on another, and then your files on another? If so.. that would be quite usefull. Would it be possible to access the files from both windows and linux? I am very intrigued by the idea of partitioning and i cant wait to get home and get started!

---

### Post by karih on 2004-11-30
[QUOTE=Infatuated_iPod]Would it be possible to access the files from both windows and linux? I am very intrigued by the idea of partitioning and i cant wait to get home and get started![/QUOTE]If you are using Windows XP you are propably using Microsofts NTFS filesystem, linux can read the NTFS filesystem but not write.  There are also tools for windows that can read linux ext2/ext3 partitions (google ext2ifs).  If you would like a partition that is shared between windows and linux and both can write to I would use the FAT32 filesystem and then you can write/read that partition from both operating systems.

So I would suggest eg 
20GB for Windows itself (C:)
10-20GB for Ubuntu Linux
Rest for shared filesystem (FAT32)
these sizes could be different depending on your needs.

---

### Post by TravisNewman on 2004-11-30
Don't forget that you may want a swap partition that's about twice as much as the amount of ram you have. If you have a crapload of ram, then you don't really need one, but if you have less than 512 megs of ram, or you're going to be running everything imaginable, I'd suggest a swap partition.

---

### Post by Infatuated_iPod on 2004-11-30
One more question, the amount that will be shared between them, can i just leave it as free space? Or do i have to format that also? Also, when i am saving a file what will the area that is shared be calleD?

---

### Post by TravisNewman on 2004-11-30
[QUOTE=Infatuated_iPod]One more question, the amount that will be shared between them, can i just leave it as free space? Or do i have to format that also? [/quote]
Anything you want to use has to be formatted with some filesystem. In this case, you'll probably want fat32

> Also, when i am saving a file what will the area that is shared be calleD?
Whatever you tell it to be. You can define a specific mount point. Mine is /storage but you can call it /media/poop, /mnt/otherdrive, or /supercalifragilisticexpialidocious if you want.

---

