---
title: "Dual-Boot: Vista Business and Ubuntu"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Tauhshi on 2007-02-20
Ok, I've already tried this:
[LIST=1]
[*]Install Vista
[*]Get depressed trying to get all my programs to work
[*]Install Ubuntu
[*]Be happy that everything works
[*]Realize that I need to use Vista for something
[*]Try to boot into Vista
[*]Fail at previous task
[*]Bang head agianst keyboard
[/LIST]

Anyway, I'm going to reinstall everything. What should I do? Vista, then Ubuntu, then some voodoo chant to make it work? Ubuntu then Vista, then Command prompt stuff and BCEdit?

SO CONFUSED!

---

### Post by rsambuca on 2007-02-21
Install Vista.  Then install ubuntu to another partition.  Grub (grand unified boot-loader) will install itself and give you a choice of Operating Systems when you boot.  Very simple.

---

### Post by unisol on 2007-02-21
#9       3 Days Ago  
 unisol  
Way Too Much Ubuntu
   Join Date: Apr 2005
Location: philadelphia,pa
Beans: 295
Ubuntu 6.06 User 

 
Re: Dual Boot Vista and Ubuntu 

--------------------------------------------------------------------------------

i found this somewhere: dual-Boot Windows Vista and Linux 
After the installation of Windows Vista, you will want to install Linux. DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to. Also, be sure to specify that GRUB is the bootloader to be installed if this is an option. After installation is completed and you will boot into the Linux operating system that you installed (because GRUB over-wrote the Vista bootloader in the MBR). From here, open up a terminal window (the method of doing so will vary across distrobutions/window managers). After you are at the terminal, all commands that are going to be needed to modify the boot menu will need to be run as 'root' so you will need to know how to accomplish this on your system (su or sudo). The first thing that we will do is backup the current boot menu, which can easily be done by doing this (remember to run this as root): 

Code: 
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 


Next, we need to edit the file "/boot/grub/menu.lst" in the text editor of your choice. You will now want to add an entry for Windows Vista. To do so, you need to add three lines to the file at the end of the file. Example entries follow: 

Vista is installed to the first partition of the first IDE hard drive: 
Code: 
title "Windows Vista" 
root (hd0,0) 
chainloader +1 


Vista is installed to the first partition of the first SATA/SCSI hard drive: 
Code: 
title "Windows Vista" 
root (sd0,0) 
chainloader +1 


If your setup is not the same as either of the examples above, you will need to modify one to match your current setup. The only area that should need modification is the line that starts with "root". The item that will likely need modification is the drive and partition information. For editing the drive that Windows Vista is installed on, you will have to change the first '0' to the number of the drive. If it is the primary or first drive, it will be a '0', the secondary or second drive would be '1', and so on. The same numbering scheme is followed for the partition information, which is the second '0'. First partition on the device is '0', second partition is '1' and so on. If you do not know what drive/partition you should put into the list, you can find this out with a disk or partition management program that may be installed with the system. If you know the device that Vista is installed on, you can also translate that to the GRUB menu. For instance, if Windows Vista is installed to "/dev/hda3" then the "root" entry would be "(hd0,2)" and if the device was "/dev/sdc5" the "root" entry would be "(sd2,4)". A general note here as well, if you have Windows Vista installed to a logical partition within an extended partition, the extended partition counts as a partition. Because of this, what would be thought of as the "second" partition, if it is logical, would actually be the third, as the whole extended partition counts as '1'. If you do not know what the entry should look like, please ask as the only stupid question is the one not asked. It will likely save time and frustration on your part. After you have the file modified, save it and now restart the system to test it out. 

Multi-Boot Windows XP, Windows Vista, and Linux 
The "triple-boot" scenario is actually not difficult, although one might suspect otherwise. The installation sequence is specific though for an easy setup. The installation procedure will be, first, install Windows XP as you normally would. After setup has finished and you are done setting things up the way you want them to be, you will want to install Windows Vista. This will alter the bootloader, and will have the Vista bootloader with an entry for Vista and Legacy OSes (XP and earlier). Once you are done with installing and configuring Windows Vista, you need to install the Linux distribution of your choice. During testing, Ubuntu 6.06 was used, and the GRUB boot menu was properly edited during installation to include an entry for Windows. Although the entry was labelled "Windows XP Professional", when this entry was selected during boot, it would bring up the Windows Vista bootloader and you could then boot either Windows Vista or a legacy operating system. There is a chance however that the installation of Linux will not automatically add an entry for Windows Vista/XP. In such a situation, one should follow the first section about adding an entry for Windows to the GRUB boot menu. 

Installation of Linux before Windows Vista 
While this situation is not the ideal situation, it is not hard to fix. This should just involve re-installing GRUB. This can be done by using the following directions. First, open up the terminal and run the following command as 'root': 
Code: 
grub 

This will bring up the GRUB shell, which will allow you to re-install GRUB. From here, you will need to specify the drive and partition that GRUB is going to be installed (or reinstalled) to. We can do that by using the following command: 
Code: 
root (hd0,1) 

There may be a few changes that need made here depending upon the current setup. First, you need to make sure the drive type is correct. If GRUB is going to be installed to an IDE hard drive, then 'hd', as shown in the example, is going to be used. Otherwise, it will be 'sd', for a SATA or SCSI hard drive. The next item, the '0', is the drive number. Zero (0) specifies that it is the first hard drive in the sequence. If it is the second hard drive, this would be changed to '1' (one) and so on. Keep in mind that numbering starts at '0' so you would take the drive number and decrease it by one for the number used here. The last number, '1' in the example, is the partition where GRUB is to be installed. This partition should be the one that contains the '/boot' directory, and again, numbering of partitions starts at '0', so the above example is installing to the 2nd partition on the physical disk. The last step would be to install GRUB to the MBR, which can be done with the last command: 
Code: 
setup (hd0) 

Which could also require editing, depending on the setup. The drive type would need changed as described above along with the disk number. Since we are installing to the MBR, you will want to specify the drive that currently contains the boot information that is used by Windows Vista. 

From here, we are now done installing GRUB to the MBR and we can exit the GRUB shell by typing: 
Code: 
quit 

After exiting the shell, we can restart the computer and test out to see if the reinstallation of GRUB was successful. If you do not have any entries for Windows, you will need to follow the instructions above in the section on dual-booting as this describes the process of adding Windows Vista/XP to the GRUB boot menu.

---

### Post by Tauhshi on 2007-02-21
Ok, I've already tried the Install Vista, then Ubuntu deal. Grub worked like a charm, but Vista refused to boot afterwards. But, I did resize the Vista partition in Gparted. Could that have been the problem? Should I:

[LIST=1]
[*]Format HDD
[*]Install Vista
[*]Resize Vista Partiton using the built in Disk Manager
[*]Install Ubuntu
[/LIST]

---

### Post by rsambuca on 2007-02-21
If you don't mind starting from scratch again, I recommend partitioning the drive the way you want it prior to installing anything, then you can just install both OS's without messing with them.  I recommend the gParted live CD, which you can find [[COLOR="Red"]here[/COLOR]]("http://gparted.sourceforge.net/")

---

### Post by koolguynet on 2007-03-05
Tauhshi,
I am curious to know....did the method rsambuca recommend work for you?

---

