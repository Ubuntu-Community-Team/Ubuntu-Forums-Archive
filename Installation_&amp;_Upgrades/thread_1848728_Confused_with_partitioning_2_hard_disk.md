---
title: "Confused with partitioning 2 hard disk"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by TweFoju on 2011-09-23
Hi guys, i am confused right now with partitioning my uBuntu and Win7

i have 2 Hard Drive on my Laptop right now

1 is SSD ( currently Win7 ) and the other one the HDD ( which is empty now )

so my idea is that on the SSD, i can have both uBuntu and Win7 (dual boot?)

but then i also want the HDD to act as storage for both the OS ( uBuntu and Win7 )

so i only intend to use the SSD as the system installation for both OS, and then when i download stuffs from either Win7 or uBuntu, i want to access the HDD for storage

can i do that?

because right now i am not sure what to do, also i am fine with uninstalling the Win7 on the SSD right now, because i just did the clean install, so i dont mind redoing it again

i hope you guys understand what i mean

thanks

---

### Post by mastablasta on 2011-09-23
> **TweFoju said:**
>  
can i do that?
 
 
 
sure you just need enough space on SSD (about 20-25GB will be plenty for Ubuntu). the easiest way is to just free this space via windows disk manager (make it raw i.e. no file system) and then install ubutnu on emty disk space. make sure you do a couple of defraging before doing the empty disk partition.
 
If you format the HDD with NTFS file system it will be accessible form both systems.
 
if however oyu want to have separate home partition (put home folder on its own partition) on the second disk then you don't need so much on SSD space for Ubutnu. but i would just install it normally to SSD giving it about 25 GB and use the HDD for data.

---

### Post by garvinrick4 on 2011-09-23
Here is a link about partitioning for you might come in handy.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by YesWeCan on 2011-09-23
I have set this up like this:
SSD - Windows 7 in one partition, Ubuntu in 20GB partition
standard MBR boot code, installed by Windows

HDD - swap partition, ubuntu home partition, ntfs partition
Grub MBR boot code

The bios is set to boot the HDD first. Windows can be booted directly by booting the SSD.


It is easy to mount the HDD partition at /home but it is more complicated with Windows to put Documents and Settings on the HDD; it might not be more complicated but I dont know how to do it. It is easy to make the ntfs partition drive D:

---

### Post by TweFoju on 2011-09-23
Thank you guys. i will try that as soon as i got back from my class, will ask questions later if i still dont get it

and thanks for the link too garvinrick4 ):P

---

### Post by TweFoju on 2011-09-25
Allright guys, back

im currently installing my uBuntu

ok, so currently, i am in the Partition Area

so as you know, i have 2 HDD ( currently Windows 7 on the Default HDD )

and new Installed SSD ( formatted to NTFS in Windows )

now

what confuse me is this:

i got to the "Something Else" option

then i got this so many options coming out

like the Device Name which is:

/dev/sda
/dev/sda1 FAT32
/dev/sda2 NTFS
/dev/sda5 NTFS
/dev/sdb
/dev/sdb1 NTFS

then at the bottom there is this list of options:

/dev/sda ATA*serial number* (750.2GB) - ok i guess that this is the default HDD of my Laptop which contain the Win7

/dev/sda1 Windows Recovery Enviroment (Loader ) - i guess i dont need this <- can i delete this partition?

/dev/sda2 Windows 7 ( Loader ) <- i guess safe to delete too?

/dev/sda5 <- ?

/dev/sdb/ ATA OCZ-Vertex3 (120.0gb) <- the SSD

/dev/sdb1



ok so now i am stuck

so what should i do to do what i want to do? =S

thanks

--------update----------

ok so i just deleted most of the partition there, now i only have 4 on the Device list:

/dev/sda
free space - 750gb HDD
/dev/sdb
free space - 120gb SSD

so  i got 2 free space now, then i go to the SSD Free space, and i select "ADD"

then it tells me to choose, Primary or Logical, since this is for the System, i choose the Primary, and i give it 40gb

then there is this option that says, "Location for the new Partition" i just choose Beginning

then use as: now this i am stuck, there are like lots of options, but i heard EXT4 is the best one now?

then Mount Point... not sure which one, /boot or /home?

---

### Post by Elfy on 2011-09-25
> then use as: now this i am stuck, there are like lots of options, but i heard EXT4 is the best one now?ext4
> 
then Mount Point... not sure which one, /boot or /home?if this is your install it needs to be /

If you want /home seperate it will need it's own partition

> then at the bottom there is this list of options:this is where it will put the bootloader - if you're not sure don't touch it

---

### Post by TweFoju on 2011-09-25
hi Forest!

so in short, what is /boot and /home for?

ok, so the Primary i set it to "/"

so now i want to make the rest of partition for Windows 7 on the SSD, but there is no NTFS available on the list

and then for my 2nd HDD ( the 750gb ) which i plan to use for both OS to access, what file system do i format it to?

FAT32?

oh and there is only 3 bootloader now, the HDD, SSD and the dev/sdb1

shouldn't i have to choose the SDD considering that i want that to be my primary?

---

### Post by Elfy on 2011-09-25
If you are going to be installing windows then I would seriously suggest that you do that first - then install ubuntu - then you'll get both on the boot list.

IF you install windows second then you will have to reinstall grub to see your ubuntu install

IF the 750Gb is for both to use for data - format that to ntfs.

/home is similar to windows docs and settings
/boot is for just boot files - I've never needed to do so and if you're only doing it because you read it somewhere else and think you might - you probably don't :)

---

### Post by TweFoju on 2011-09-25
oh ok, let me install my Win7 first, ill be back shortly

please help me through the partition settings step by step after i finish installing the Win7 ;)

i really am suck for learning new system even when i read the partition thread, still dont get it =(

---

### Post by Elfy on 2011-09-25
If I'm about - I will, though I doubt I'm the only one reading this :)

---

### Post by TweFoju on 2011-09-25
sorry i have a question

what do you mean when you say if i install uBuntu then Windows, i will lose my Grub?

so, it's a taboo to install uBuntu before Windows?

---

### Post by westie457 on 2011-09-25
> **forestpiskie said:**
> If you are going to be installing windows then I would seriously suggest that you do that first - then install ubuntu - then you'll get both on the boot list.

IF you install windows second then you will have to reinstall grub to see your ubuntu install

IF the 750Gb is for both to use for data - format that to ntfs.

/home is similar to windows docs and settings
/boot is for just boot files - I've never needed to do so and if you're only doing it because you read it somewhere else and think you might - you probably don't :)

+1 for the advice.

To the OP.
Here is a link to what I would do and also have done to have a dual-booting system. [http://ubuntuforums.org/showpost.php?p=11107302&postcount=5]("http://ubuntuforums.org/showpost.php?p=11107302&postcount=5")

The other hard drive I would have one partition on formatted to NTFS and use it for data storage only.

This is just my personal choice and is not something set in stone.
If you definitely want 2 or more partitions on the 2nd HD say so and you will get some recommendations for that as well.

---

### Post by TweFoju on 2011-09-25
no, it's ok

i only want my 2nd HDD to contain movies, and all my work

since in the uBuntu partition, you cannot do NTFS, i guess you have to format it on Windows?

---

### Post by westie457 on 2011-09-25
Once you have installed Ubuntu you should be able to format to NTFS using Gparted.

Depending on which version of Ubuntu you are installing Gparted is installed. If you are installing 11.04 you will have to install Gparted either through the Software Centre or the Command Line (Terminal).
The command to use in the terminal is ```
sudo apt-get install gparted
```

You certainly can format a partition to NTFS using a LiveCD.

---

### Post by TweFoju on 2011-09-25
Thank you, im currently installing the Windows, ill try it out later once i got back to the uBuntu partition part

o yeah 1 more thing, is gParted work with 64bit OS? because i see they are made based from 32 system?

---

### Post by westie457 on 2011-09-25
I see no reason why it should not work on the partitions. Though I cannot say for definite as all my laptop and desktop pc are only capable of using 32-bit operating systems.

---

### Post by Elfy on 2011-09-25
worked fine with 64bit last time I used it on 64bit

---

### Post by Elfy on 2011-09-25
> **TweFoju said:**
> sorry i have a question

what do you mean when you say if i install uBuntu then Windows, i will lose my Grub?

so, it's a taboo to install uBuntu before Windows?

It's not taboo - nor do you HAVE to do it that way - it is though much easier :)

---

### Post by YesWeCan on 2011-09-25
> **forestpiskie said:**
> ext4
if this is your install it needs to be /

If you want /home seperate it will need it's own partition

this is where it will put the bootloader - [COLOR="Red"]if you're not sure don't touch it[/COLOR]
Ouch! The Ubuntu installer default causes so many problems.

DO NOT install the boot-loader (aka Grub) to the SSD which has your Windows installation. Install it to the HDD. Then tell the BIOS to boot from the HDD. :)

---

### Post by Elfy on 2011-09-25
> Ouch! The Ubuntu installer default causes so many problems.
It also doesn't.

---

### Post by TweFoju on 2011-09-26
anyway, installation on hold until i get a new motherboard

something happened to my laptop, lol

was updating BIOS after i finished my Windows installation, but it just had to happen this  time :mad:

---

