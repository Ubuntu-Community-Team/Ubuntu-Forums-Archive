---
title: "More XP/Ubuntu boot problems..."
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by prezet on 2006-07-08
ok, I've now got ubuntu installed alongside XP.

Set up as follows:
XP NTFS 90G Primary
Ubuntu Ext3 14G Primary
- Swap 1G
- OS Share 20G

When I got to the install of GRUB I installed it directly into the root of the Ubuntu partition.

Now when I boot, it's bypasses GRUB and boots directly to XP. Have I missed somethinng?

---

### Post by Athropos on 2006-07-08
The first place used when booting is the Master Boot Record (MBR). In your case, the MBR points to the Windows partition, so when you boot you are directly taken to Windows (as requested by the MBR).

The correct way *could* have been to install Grub in the MBR, in order to launch Grub upon booting. Grub would allow you to choose between your two systems.

---

### Post by Herman on 2006-07-08
Don't worry, it's not too late, if you have the 'Alternate' install CD, you can install GRUB to your MBR without the need for a complete reinstall, just use 'Rescue a Broken System' Mode, to see that illustrated, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub").
Regards, Herman :D

---

### Post by prezet on 2006-07-08
Well I reinstalled just to be on the safe side...

Now I get the following message:

GRUB loading, please wait...
Error 17

????!???? Whats happened ????!????

---

### Post by Herman on 2006-07-08
Grub is the only bootloader that I know about that can set itself up automatically most times without needing o be manually edited. But unfortunatley for you there seems to be something that needs to be corrected in grub's configuration to get it working properly for you in htis machine. 
There are two ways to go about this. 
1) you can use grub's command line interface to find out the right commands to load Ubuntu and boot that way. 
Then, edit your /boot/grub/menu.lst file with the same commands you just used to boot from CLI with.
[*Click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst") for more about grub's menu.lst
For more about how to use GRUB's Command Line Interface, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
2) You can use a Live CD to run the following command ```
sudo fdisk -lu
```, and have a look at your /boot/grub/menu.lst and see if anyone can spot the error and help you with it, (post the fdisk and menu.ls here).
You may need to mount your Ubuntu partition and open your /boot/grub/menu.lst like this, [*click here*]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") to see how.
I hope one of those two methods will get grub working properly for you without too much trouble, most of the time either of those two methods will work. Don't forget to post here for more help if you need it. Regards, Herman :D

---

### Post by prophet11 on 2006-07-08
i have a quick question, im going to do the same but im not sure of his specs if it will appl yot me, i mgoing to be putting linux on my other HD i will have XP on my main HD do i need to install GRUB on the partion on the HD that will have ubuntu or on the HD that has XP, i assume the one that will have Ubuntu?

---

### Post by Herman on 2006-07-08
> i have a quick question, im going to do the same but im not sure of his specs if it will appl yot me, i mgoing to be putting linux on my other HD i will have XP on my main HD do i need to install GRUB on the partion on the HD that will have ubuntu or on the HD that has XP, i assume the one that will have Ubuntu? I think what normally works best for most of the time is to install GRUB to MBR on the first sector of the first track of the first hard disk. The first track (63 sectors) of most hard disks is usually empty and reserved for things like bootloaders, so it is not part of any filesystem that belongs to a particular operating system. The MBR is the first sector of that first track. That is where the BIOS will look for instructions as to how to boot the computer. This will point the BIOS to the partition that owns the bootloader whose IPL is written there (in the MBR).

You can also install a bootloader to the first sector of an operating system's partition, but then it will only be good for booting that one single operating system and it will need to be 'chainloaded' from another bootloader (like a relay switch in a car). GRUB is too good for that, it would be a waste to use Grub that way. Instead I install Lilo to the first sector of my Ubuntu partition as an emergency boot method in case I make a mistake with GRUB and need to use GAG Boot Manager to boot Ubuntu to fix GRUB. (I do that some time after the install is finished).

Prophet11, your setup, with XP on your first hard drive, should be good, as Windows likes to be first generally. I don't think it's much of a problem for most people, I think the Ubuntu installer (and GRUB) will just get it set up right automatically nearly every time. You probably don't need to worry about it. Just go ahead and let the installer automatically install GRUB to MBR.
Compared to the number of people installing Ubuntu every day, only a very small percentage would have any problem, and mostly if there is a problem it is easily corrected. Occasionally it is something difficult, but that is rare.


Good Luck, Regards, Herman :)

---

### Post by prophet11 on 2006-07-08
So just to make sure GRUB goes on the first volume which is the first hard drive that has XP partition on it..

---

### Post by Herman on 2006-07-08
> So just to make sure GRUB goes on the first volume which is the first hard drive that has XP partition on it..Yes, the Ubuntu installer and Grub will handle that automatically for you. 
Yes, in your machine with XP on the first hard disk it goes on the disk with XP on it. It does not make any difference wht operating system happens to be on the disk, the first track is not part of that operating system's filesystem.

If you had no operating system at all on the first hard disk (maybe data partitions for example), the MBR on whatever disk the BIOS thinks is your first hard disk will still be the place where the BIOS will look for the MBR. Even with no operating system at all there, the Ubuntu installer will still probably install GRUB to MBR on your first hard disk.

If you wanted to install Ubuntu on the first hard disk and you had XP on the second hard disk and then the installer will (should) still install Grub to MBR on the first hard disk. You would probably need to use a pair of 'map' commands to trick Windows into thinking it is on the first disk to make Windows boot okay in that situation.

If you have IDE and SATA disks mixed together sometimes Grub has a hard time deciding which is the first disk and you might find grub installing to the wrong one. If that happens then you just have to  re-install grub to the correct one. (The one your BIOS thinks is your first one). There are lots of ways to re-install grub anywhere you like, (or lilo).
Regards, Herman :D

---

### Post by prophet11 on 2006-07-08
i think i have all 3 of my drives set correct master xp slave extra HS and slave master will have Ubu so i think it should find the right ones.

PS i have Live CD and Alternate what should i use?

---

### Post by Herman on 2006-07-08
If you are worried about the possibility of temporarily loosing the ability to boot Windows quickly should something go wrong, it is a good idea to download yourself a copy of GAG Boot Manager, which is free, and only a small download. You can make yourself a GAG Boot Manager CD-ROM, or floppy disk to boot Windows with until you have time to sort out any grub issues. It allows you feel a lot less stressed in the meantime.
[*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm") for a how-to on GAG Boot Manager. There is a link to a download site there too.
Regards, Herman :)

---

### Post by prophet11 on 2006-07-08
Na im not scared of messing up windows i reformatted 2 weeks ago i dont care im confortable with doing stuff its just that i want to be sure i do it right the first time..

---

