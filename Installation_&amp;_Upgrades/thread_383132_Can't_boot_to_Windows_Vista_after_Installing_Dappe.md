---
title: "Can't boot to Windows Vista after Installing Dapper as dual boot on Acer laptop"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by marklg on 2007-03-12
I used Windows to make room on one of three partitions existing on new Acer Aspire 5610 and installed Ubuntu successfully. When I try to boot to Vista using GRUB menu, Windows XP boot page appeared for a while, then Acer "eRecovery Management" appears. Recovery gives three choices: 1. Restore to default, 2. Restore from Recovery CD set, 3. Exit. None of the three has an effect on the result, i.e., to loop back through the same things. I suspect that the /boot/grub/menu.lst file's final selection for non-linux OS is at fault but I don't know how to fix it. 
Relevant part of file says: /dev/sda1
title: Windows NT/2000/XP
root  (hd0, 0)
save default
makeactive
chainloader +1

Original Partition state as follows:
Partition1 Acer Recovery 6.8 GByte  /dev/sda1
Partition2  C Drive  34 Gbyte           /dev/sda2
Partition3  D Drive   33.7 GByte       /dev/sda3

Changed to:
Partition1  unchanged
Partition2  unchanged
Partition3  reduced to 25.9 GByte
Used Ubuntu to fill free space giving: Ext3  7.6GByte  /dev/sda5 and 
SWAP  360MByte /dev/sda6

Any suggestions please? I didn't even get acquainted with Vista before I vanished it and I would like to keep it until I get to know Ubuntu Linux.

---

### Post by ssican on 2007-03-13
Perhaps this can help. See  -CUSTOMIZING YOUR DUAL-BOOT SET UP-  and  -SETTING UP A DUAL-BOOT CONFIGURATION(for Windows XP)-   in this link : [http://doc.ubuntu.com/ubuntu/switching/C/dualboot.html](http://doc.ubuntu.com/ubuntu/switching/C/dualboot.html)

---

### Post by ssican on 2007-03-13
There is other TUTORIAL very good that can help. See the end of the tutorial.  [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by unisol on 2007-03-13
i dont use vista,but i found this on the internet;Dual-Boot Windows Vista and Linux 
After the installation of Windows Vista, you will want to install Linux. DO NOT resize the Vista partition during the installation of the Linux distribution! Due to the change in NTFS versions, no Linux partitioning program, nor standard Windows partitioning programs, can properly alter the partition that Vista is installed to. Also, be sure to specify that GRUB is the bootloader to be installed if this is an option. After installation is completed and you will boot into the Linux operating system that you installed (because GRUB over-wrote the Vista bootloader in the MBR). From here, open up a terminal window (the method of doing so will vary across distrobutions/window managers). After you are at the terminal, all commands that are going to be needed to modify the boot menu will need to be run as 'root' so you will need to know how to accomplish this on your system (su or sudo). The first thing that we will do is backup the current boot menu, which can easily be done by doing this (remember to run this as root): 

Code: 
cp /boot/grub/menu.lst /boot/grub/menu.lst.bak 


Next, we need to edit the file "/boot/grub/menu.lst" in the text editor of your choice. You will now want to add an entry for Windows Vista. To do so, you need to add three lines to the file at the end of the file. Example entries follow: 

Vista is installed to the first partition of the first IDE hard drive: 
Code: 
title         "Windows Vista" 
root         (hd0,0) 
chainloader      +1 


Vista is installed to the first partition of the first SATA/SCSI hard drive: 
Code: 
title         "Windows Vista" 
root         (sd0,0) 
chainloader      +1 


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

After exiting the shell, we can restart the computer and test out to see if the reinstallation of GRUB was successful. If you do not have any entries for Windows, you will need to follow the instructions above in the section on dual-booting as this describes the process of adding Windows Vista/XP to the GRUB boot menu. hope it helps.

---

### Post by marklg on 2007-03-13
Thanks for the help. I have tried many different combos of menu.lst settings. I have no explicit info that the HD is SATA but Ubuntu refers to it using sda nomenclature. When I use (hd0,0) in MENU and try to boot to Vista, I get the ACER Recovery Pro gram. For other values of hd, e.g., (hd2,0); (hd1,0); the following is displayed: "Error 21: Selected disk does not exist". When the values: (sd0,0); (sd1,0); (sd2,0); (sd3,0); (sd0,1); (sd0,2); (sd0,3); are used "Error 23: Error while parsing number" comes up.

There is one HD and the original 3 partitions are now 5 (see my first post). Since Vista is on the 2nd partition, the correct menu.lst entry should be sd0,1. Is this correct?

I can't use any disk or partition management except what Ubuntu provides since I can't access Vista.

Installing Linux before Vista doesn't apply so I do not understand whether the procedure you describe to do this is relevant.
Ubuntu boots up just fine, the problem is that Vista doesn't. :confused:

---

### Post by ssican on 2007-03-14
The method described(on doc.ubuntu.com in the link of the post2) with the title "Customizing your dual-boot set up" is applied for (tri)Multiboot set up. This method is used in the tutorial of the APCmagazine refered no post 3. The link of the post 3 is for "VISTA INSTALLED FIRST"  (Linux after Vista).  APCmagazine have also tutorial for Linux installed first.   For just Boot any OS  at Multiboot set up, may to be used -SGD- Super Grub Disk. See screenshots on : [http://linux.softpedia.com/progScreenshots/Super-Grub-Disk-Screenshot-8071.html](http://linux.softpedia.com/progScreenshots/Super-Grub-Disk-Screenshot-8071.html)

---

### Post by scxtt on 2007-03-14
if you've only got 1 disk, your only options are:

hd(0,0)
hd(0,1)
hd(0,2)
etc.

judging from your 1st post, you'll probably want to use something like "(hd0,4)" or "(hd0,5)" ... maybe "(hd0,6)" :p

---

### Post by ssican on 2007-03-14
Another option is make use of method of FixMbr - using the Vista installation DVD -  So, Vista will overwrite MBR and Grub will be Lost. When you reboot into Vista, Linux is nowhere to be seen.  This method is on: [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)      
For to access Ubuntu you will need   1)Reinstall GRUB and   2)Create the Linux Boot option in Vista (methods described in APCmagazine on [http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

---

### Post by marklg on 2007-03-14
Using (hd0,1) in menu.lst did the trick. Thanks to you, scxtt, and unisol for the help and for making my first forum visit helpful and pleasant.

---

