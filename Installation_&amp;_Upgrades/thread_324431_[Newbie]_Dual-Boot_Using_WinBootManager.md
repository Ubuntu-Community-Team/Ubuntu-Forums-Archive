---
title: "[Newbie] Dual-Boot Using WinBootManager"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by pmcastillo on 2006-12-23
First, I installed the WInXP,

Then, I installed Ubuntu,

Now, my Boot Manager was changed to GRUB,

Is there any way to change it back to WinBootManager for dualboot?


<-------------- Newbie here :(

---

### Post by bulldog on 2006-12-23
Is there a special reason why you want that?
Grub works fine and you'll get used to it.

But if you want you can surely install another boot loader.

---

### Post by meng on 2006-12-23
You can easily tell grub to load Windows by default if that's what you want. I don't think the Windows boot manager is configured for dualbooting!

---

### Post by pmcastillo on 2006-12-24
Ummmmm... I'm still comfortable with Win Boot Manager... I did some research on the internet and I found this... [http://aruljohn.com/info/dualboot.php](http://aruljohn.com/info/dualboot.php) It tells:

* Removing Grub (and installing Windows bootloader)
* Windows NT bootloader as the default bootloader
* And many more...

I got confused with the steps

> 
01:  Windows 2000 has to Own the MBR - you can't install LILO in it.


**QUESTION NUMBER 1**: What's the difference between Master Boot Records (MBR) and the Boot Records? Or is there any diference?

> 
02: When you install linux, install LILO on the root install partition instead & make a boot disk when prompted.


**QUESTION NUMBER 2**: What is root install partition?

> 
03: Then, when linux is done installing, boot it from the disk.
04: Mount a new msdos floppy and type:

dd if=/dev/hda6 bs=512 count=1 of=/linux.bin
(here, hda6 is the root partition, you can substitute it for your own linux root partition)


**QUESTION NUMBER 4**: What is "mount"? Is it like putting the CD on the CD Tray?
**QUESTION NUMBER 4**: What's the meaning of the "dd" command?

> 
05: Now you need to copy the MBR to the floppy
mount -t msdos /dev/fd0 /mnt
cp /linux.bin /mnt
umount /mnt

06: Remove the floppy from the drive and reboot in Windows 2000.
07: Copy the linux.bin file from the disk you just used to the root of your C drive.
08: Edit c:\boot.ini and add an entry at the end that looks something like this: c:\linux.bin="RedHat 7" or whatever you want to call it.
09: The NT bootloader will now launch LILO when you choose RedHat from the menu.


---

### Post by bulldog on 2006-12-24
Maybe you should do first some exploring before you attempt to install.

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by Unc0 on 2006-12-25
bulldog is right, try doing some research first before you go doing things like this. the way it is now is quite messy. did you prepare your hard drive before insalling linux? you want to have some un-partitioned space on your hard drive after the windows installation to make life easier.

unfortunately, there doesn't seem to be a lot of information out there for ubuntu multiboot systems using the windows boot manager. 

to answer your questions briefly:

1. the MBR is the first section of the hard drive that an operating system will refer to in order to pull itself by its bootstraps. the windows boot manager has to be installed on the MBR otherwise windows won't boot. the regular windows user doesn't know this because there's no need to know this if you're only using windows.

2. i'm guessing "root" is a typo here and it should be "boot". you can install LILO on the first sector of the boot partition, the /boot partition should have been created during the initial linux setup. this means that it will be installed on a free section of the hard drive other than the MBR. you would then need to boot linux from a floppy. you get the opportunitiy to create a boot floppy at the end of the linux installation.

3. it's making the OS aware that there is a floppy drive with a disk in it.

4. google is your friend. dd - convert and copy a file. but you don't need to know this. just follow the instructions.

sounds to me like you would probably be better off starting from scracth (both windows and linux). format your hard drive and create a small partition for your windows OS. leave some un-partitioned space on the hard drive and partition it manually during the linux installation. do some research.

---

### Post by Unc0 on 2006-12-25
having said all that. why don't you just let GRUB boot your windows OS?

---

### Post by bulldog on 2006-12-25
> **Unc0 said:**
> having said all that. why don't you just let GRUB boot your windows OS?


:D :D :D ;) Did ask him the same question.

---

### Post by great1 on 2006-12-25
I am new user for the Ubuntu its looking cool.At the same time i feel its like too much to know about commands and all

But still I love it its different from any other of its kind

Any way as i am very found of games i want win xp and ubuntu to learn

problem is 

I have installed the ubuntu copy in my complete 160Gb hard disk
and if I had to install windows xp what problem do i have to face and 
please help me install windows also
so that i can get both

---

### Post by bulldog on 2006-12-25
If there's no important data in your Ubuntu install [whole disk] just repartition and install windows first.

You can use the partitioner Qparted on the ubuntu live cd,but I prefer the Gparted live cd [30MB download]

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Burn this ISO to an Image and boot from it,you'll end up with seeing your hard disk with a graphic interface.
Some suggestions,I presume you'll be using windows for the most part.

Delete all the partitions which are on the disk so you'll have 160GB of unallocated space.
Right click the space and choose create new partition.
Make a 100GB windows partition or make two or more if you want,just keep in mind you can have only four primary partitions,if you want to have more partitions,no problem,create 3 primary's and from the rest of the space create a extended partition.
In this extended partition you can create a bunch of logical partitions if you like.

Okay,create  a 10GB, primary or logical at your choice,and format it ext3 this will be the / (root) partition
Create a 1GB swap and format it as swap.
If you have space left :D  create a partition which can be your /home for ubuntu.

Now install windows on the first primary and install ubuntu afterwards.
When you come to the partitioner when you install ubuntu,choose manual partitioning [already done] and mount the 10GB partition as / ,the 1GB swap as swap,and if you have created another ext3 partition for /home mount it as /home.
Set this two partitions to reformat ext3 and the swap as swap,and check your windows partition is not set to format!!!
Continue the install and you'll end up with a nice dual boot system,with GRUB as the boot loader,which gives you the opportunity to choose which OS you want to boot,ubuntu is set as the default though,but we can change that.

Good luck

---

