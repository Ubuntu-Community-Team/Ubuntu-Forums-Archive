---
title: "ubuntu won't intall on master drive"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by JKtheunwise on 2007-11-14
I have tried to install ubuntu v. 6.06 from live CD - it seemed to work ok but I have 2 hard drives and it seems to have to installed on the slave drive rather then the master. So when the computer starts up again it just boots to windows  vista as normal?

I have tried using the live C.D. again to install to master drive but it doesn't seem to give me that option in the graphical interface.

Please assume I know very little (I don't), I have tried to search for a solution but can't really understand any of the info I have found.

My computer:
Fujitsu Siemens, Intel core 2 CPU, RAM 1022, 32 bit operating system
Windows vista home premium 

2 Hard drives:

Master (drive that came wif computer):
Has windows installed, seems to be partitioned into
- System (c:) 173 GB
- Data (D:) 45.2 GB

Slave (drive from my old computer which I installed):
- K drive (F-J are memory card slots)
Ubuntu seems to have installed itself here
but when the commputer switches on it boots to windows vista?
Since I tryed to install ubuntu this drive has disappeared and is imposible to view using the file explorer on vista??

Any help would be appreciated, I hate vista and would really like to give ubuntu a try.

---

### Post by kyphi on 2007-11-14
I don't quite understand if you want to have a dual boot system with Vista on one drive and Ubuntu on the other or if you want to wipe out Vista with Ubuntu.

The way you have your computer set up now, Vista cannot see the other hard drive because Ubuntu is installed there and Ubuntu uses a different file system to Vista.

I am not familiar with Vista but in XP you can right click on the 'My Computer' icon on the desktop and select 'Manage' from the dropdown menu which will show you your two drives and how they are partitioned.  Perhaps that works in Vista too.

Ubuntu does not install itself on any drive that it chooses - you must make that choice.  Possibly you have not installed GRUB, the bootloader, in the right place.

The best option at the moment seems to be to reinstall Ubuntu to your second drive.

If you are using PATA drives (connected via ribbon cable) you need to make sure that the jumpers for master and slave drive are correctly set.  If you are using SATA drives (thin, coloured cable) there is no need to do this.

---

### Post by JKtheunwise on 2007-11-14
umm ... idealy I suppose I'd like vista on the old drive and (it is currently on the new) and ubuntu on the old.

> Ubuntu does not install itself on any drive that it chooses - you must make that choice. Possibly you have not installed GRUB, the bootloader, in the right place.

Well it doesn't seem to give me the option to install on the new drive. First time I tryed to install it came up only with one drive and unthinkingly I clicked yes - but I now realise that it was the slave drive rather then the master. When I try again - it doesn't give me the option to load on the C drive only the K!

I don't know what the Grub is, I have been trying to install form a live CD in my CD drive.

the following picture shows how my drives are petioned using the manage function as you suggested:
[[IMG]http://img249.imageshack.us/img249/4705/diskpartitionsjj4.th.jpg[/IMG]](http://img249.imageshack.us/my.php?image=diskpartitionsjj4.jpg)

I think that the new drive (master) is SATA and I haven't messed with how it was set up when it came in the computer, the old drive (slave) is PATA and I set the pin thing up for it to be a slave drive (though i suppose I could have messed it up - but it worked fine and  got all the old data off it?).

---

### Post by kyphi on 2007-11-15
The only way to get Vista onto the old drive is to freshly install it there.  For that you need your Vista installation CD or DVD.

Vista MUST be installed first.  Otherwise it will wipe the boot record of Ubuntu.

So, to get Vista onto the old drive, you must first totally remove it from your new drive by formatting the drive.  After that, what I would do is to disconnect the drive.  Then reinstall Vista, this time on the old drive.

Reconnect your new drive and install Ubuntu to that.

You should end up with a dual boot system.

GRUB stands for **GR**and **U**nified **B**ootloader

---

### Post by JKtheunwise on 2007-11-15
Just realised I don't have the CD, the computer came pre-installed with vista.

What do i do if I just want to have ubuntu?

---

### Post by kyphi on 2007-11-15
If you want to have Ubuntu only, you can either:

1. take out the Vista drive, store it in your shed, in case you want it in the future and buy another SATA drive to install Ubuntu on.  Then install Ubuntu on the whole drive - if you tell Ubuntu that it can have the whole drive it will partition and install automatically.

2. While you still have Vista, go into Manage again and destroy the partitions (this will annihilate Vista) so that there is only one partition (from memory you have to click on a partition or right click and you will get the option to remove a partition) and then install Ubuntu to that drive.
With your intervention, Ubuntu can reorganise the existing partitions on your Vista drive and wipe Vista in the process.

First, I would remove the drive you installed.  Old and new technology does not mix too well and your newer drive is big enough for years to come.  I run an 80 GB drive with 60 GB free at the moment but I also use a backup USB drive of 60 GB.

What would you like to do ?

---

### Post by JKtheunwise on 2007-11-16
I'm not sure what to do, I suppose the question is, will I need windows or am I prepared to just stick abandon all and go for Ubuntu?

My anti-microsoft, pro-free and open source software view makes me want to go for it but will I regret it? I guess if it all goes wrong i could just get a computer shop to reinstall vista for me as i have the code number for it.

I now have a 500GB external hard drive so I suppose I could remove the old drive, I only really put it into so I could transfer data off it.

Still not sure I understand why the live CD didn't let me select the main drive in the first place?

Also, when I click destroy the partitions and this will annihilates Vista, i will be in Vista, so what will happen? Will the computer switch off? how will i install Ubuntu if i have no opperating system to start with? Will I need to do stuff in DOS, I don't know anything about that :-| or will I still be able just to instert the CD again?

---

### Post by pcjunkie on 2007-11-16
> **JKtheunwise said:**
> I'm not sure what to do, I suppose the question is, will I need windows or am I prepared to just stick abandon all and go for Ubuntu?

My anti-microsoft, pro-free and open source software view makes me want to go for it but will I regret it? I guess if it all goes wrong i could just get a computer shop to reinstall vista for me as i have the code number for it.

I now have a 500GB external hard drive so I suppose I could remove the old drive, I only really put it into so I could transfer data off it.

Still not sure I understand why the live CD didn't let me select the main drive in the first place?

Also, when I click destroy the partitions and this will annihilates Vista, i will be in Vista, so what will happen? Will the computer switch off? how will i install Ubuntu if i have no opperating system to start with? Will I need to do stuff in DOS, I don't know anything about that :-| or will I still be able just to instert the CD again?

You could make a total copy of that drive and store it.....

Ghost or similar will do that nicely....If you need to just install that drive and boot up....

---

### Post by bulldog on 2007-11-16
Your grub is probaly installed on the other hdd.
Change the boot order in your BIOS so you boot the old hdd.
If this let you boot into ubuntu,you only have to make an entry for Vista in menu.lst if you wish.

---

### Post by kyphi on 2007-11-16
I have checked on the issue with Vista deleting its own partitions via 'Manage' and that will not work.

About not having an operating system there is no need to worry - when computers come out of the factory they are not born with Vista or Linux.  They do come with the BIOS, which stands for **B**asic **I**nput **O**utput **S**ystem which will start the computer and make it ready to accept installation of an operating system.

Why Ubuntu would not install on the drive of your choice I cannot say.  Perhaps you overlooked a screen that asked you where you wanted to install to; perhaps Ubuntu did not like the setup with PATA and SATA controllers.

The ideal solutions would be either to install another SATA drive for Ubuntu or partition the Vista drive to make room for Ubuntu.  Then you can dual-boot if you want to.

I have a dual boot setup on identical separate SATA drives - that way, if one drive ceases to function (and they do that sometimes) I still have one functioning operating system.

---

### Post by JKtheunwise on 2007-11-21
I think i am going to go down the just go with ubuntu route, if it doesn't work out I can always go to a computer shop and get them to reinstall vista.

One last question before I do. I have backed up all my files on an external hard drive. Ubuntu uses a differnt file system to windows. Does this mean that I want be able to load the files stored on the external hard drive onto the main hard drive once it is running ubuntu? If so is there anyway round this (I need the work stoed on there and I want the MP3's)

---

