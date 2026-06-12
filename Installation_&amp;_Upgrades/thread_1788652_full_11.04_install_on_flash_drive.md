---
title: "full 11.04 install on flash drive"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by user987 on 2011-06-23
i created a live cd usb drive and have sucessfully been able boot up my netbook and been using ubuntu 11.04.

i now want to take the next step and install it on another usb drive.

when i am on my live cd usb in ubuntu, there is a install ubuntu icon,

do i click on it and follow the steps after i put a new usb drive into my netbook to install on the new usb drive?

if suceesful would i then have fully portable os on a flash drive that can be use on any computer?

---

### Post by mikewhatever on 2011-06-23
Yes, in general terms, that's about it. However, there are a couple of things you might want to know:

- 11.04 requires 5GB or more of free space. The resulting installation is smaller then that, but you'll get an error if installing to a smaller partition.

- Go with the 'Something else' option at the partitioning stage. This way, you can make sure the bootloader goes to the MBR of the right device (the flash drive).

---

### Post by C.S.Cameron on 2011-06-23
Following step by step for Full install of 11.04 to USB device. A full install of 11.04 requires a minimum of 4.4GB. 
Partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

### Post by user987 on 2011-06-23
hey, thanks to you 2 guys.

it look like i got the full install on my 16g flash drive and log on  to my computer and typing this note using the drive.

just one fast question can you explain why i needed to create those other partions, like home, swap etc.


:popcorn:

---

### Post by Decaffienated46 on 2011-06-24
You need to create, or let Ubuntu create, those other partitions because they are part of the linux/Ubuntu file system, like windows requires the \Windows, \Program Files, \Users, and other folders.  In the case of Ubuntu, the /Home folder is a parallel of Windows´ \Users folder. It´s where all the registered user accounts are created. The /Swap folder is kind of similar th the \tmp or \Temp Files folders in Windows.  It is the system´s scratch-pad for files that are loaded by a program, but are not immediately needed in memory. BTW, linux is much more memory, and HDD real estate efficient than Windo$e ever was.
HTH, Decaffienated46

---

### Post by Herman on 2011-06-24
Dividing your disk into multiple partitions is optional.
I personally prefer most times to install in one single / partition without any swap area, and after Ubuntu is installed I install 'Dynamic Swap Space Manager', which saves me quite a lot of disk space by dynamically adjusting the swap file to the size needed, and most of the time I don't need much swap. I set the swappiness to 10 too.

The ability of Gnu/Linux operating systems to be installed in many partitions is sometimes an advantage when dealing with a number of small disks, for example in my eeepc with a 4gb SSD and a 16gb SD card, I use the 4GB as / and the 16gb SD as /home. That makes it possible to have a workable set-up. Otherwise the amount of disk space just wouldn't be enough to do anything much.

Some people who like to install in multiple partitions use different file systems and file system mount options for various partitions too, I have an installation with some reiserfs and some ext4 partitions because somebody said it can give a speed advantage so I wanted to try it. It could be a little faster, I measured with benchmarking software but for mine at least, the difference seems marginal.

Another idea is to have more than one operating system sharing some of the partitions, for example you can install a different version or different flavor of Ubuntu or even some other Gnu/Linux distro and have them share the same swap area and the same /home partition and files. That saves disk space and provides convenient access to the shared files and can be a pretty cool trick!
The /boot partition is one partition that can't (easily) be shared.

 If you want you can have a separate /usr, /var, /tmp, /boot, /home and / and maybe more separate partitions for different folders.

Disadvantages of dividing your installation up into too many partitions are that partition sizes are relatively rigid and sooner or later if you didn't plan ahead well enough one will fill up while another has plenty of spare room and you'll need to use a partition editor to resize your partitions, which can be tricky and time consuming.
You'll also have more file systems requiring file system checks, and that can slow done your boot times. Simply having more file systems to mount slows down boot times too, even with no file system check.
Having many partitions is not an efficient use of disk space either, because you'll have more file system overheads and need to leave plenty of breathing room in each one, about 20% at least, and you also need to allocate extra space for an often unpredictable amount of future files or face the need to resize with a partition editor at a later date.

Contrary to what a lot of people like to imply, having s separate /home does not in any way excuse you from the need to make normal backups of your files to some other media regularly.
It can though make re-installing easier if the other part of your operating system has a problem you don't know how to fix and re-installing seems quicker. 
In that case you'll most times not need to re-install your /home files and settings, as you can re-install the other partitions and have the new installation mount the same old /home again as long as you don't format it. A lot of people think that's handy.

Whichever way you decide to do things, install in a single partition like I normally do or divide into as many partitions as you can, Gnu/Linux operating systems offer you the flexibility to create a wide variety of partitioning schemes and almost every Gnu/Linux user has their own personal preferences and will argue that their ideas are superior to everyone else's.
It's all part of the fun of Gnu/Linux. :)

---

### Post by user987 on 2011-06-24
hey,
         thanks to everybody for the help and insight.

i really love the idea of being able to boot up and run off  the flash drive.

it is slower than my built in 32G solid state hard drive with window xp os, but i believe that is due to the fact that ssd are built to be able to handle the os, where as the external flash drive is design as a general storage device.

---

### Post by C.S.Cameron on 2011-06-24
> **user987 said:**
> hey,
         thanks to everybody for the help and insight.

i really love the idea of being able to boot up and run off  the flash drive.

it is slower than my built in 32G solid state hard drive with window xp os, but i believe that is due to the fact that ssd are built to be able to handle the os, where as the external flash drive is design as a general storage device.

USB2 is much slower than SATA, hopefully USB3 will be an improvement, but I have not seen any reports yet of running Ubuntu from an USB3 drive.

---

### Post by user987 on 2011-06-24
i just check in the main screen  on top places and chose computer and it shows my 3 drives.

my internal 32G window XP OS  drive, my 16G  sd card as file system, and my usb flash drive with ubuntu OS as file system.

the first 2 drives shows the correct total  Gigs

the ubuntu  drive under properties shows 3.6G for contents and 814 M for free space.

the flash drive is i 16G drive, where did the other Gig go?

when i am in window and i click on properties for the C drive it shows the total C drive and free space.

i also log in to window and then plug the ubuntu drive in to see the total in properties and it shows 987M

so i am confuse on what happen. it should under windows show 16G total.

but right now my running and using ubuntu from the flash drive is working great.

if anyone can clear this up on the memory it would be great.

maybe i am not accessing the total picture since i am a newbie in ubuntu navagation.

---

### Post by C.S.Cameron on 2011-06-24
> **user987 said:**
> i just check in the main screen  on top places and chose computer and it shows my 3 drives.

my internal 32G window XP OS  drive, my 16G  sd card as file system, and my usb flash drive with ubuntu OS as file system.

the first 2 drives shows the correct total  Gigs

the ubuntu  drive under properties shows 3.6G for contents and 814 M for free space.

the flash drive is i 16G drive, where did the other Gig go?

when i am in window and i click on properties for the C drive it shows the total C drive and free space.

i also log in to window and then plug the ubuntu drive in to see the total in properties and it shows 987M

so i am confuse on what happen. it should under windows show 16G total.

but right now my running and using ubuntu from the flash drive is working great.

if anyone can clear this up on the memory it would be great.

maybe i am not accessing the total picture since i am a newbie in ubuntu navagation.

Windows can only see the first partition on a flash drive.

(Never try to format a multi partition flash drive in Windows).

---

