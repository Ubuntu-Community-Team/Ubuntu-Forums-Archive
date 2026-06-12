---
title: "Vista, XP, now installing Ubuntu 7.10 partition layout"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by speed3b on 2008-04-11
My laptop came preinstalled with Vista. I split the HDD and made a partition for XP and installed it. Reloaded the BCD bootloader for Vista and added XP Using EasyBCD. All is working fine. I want to add Ubuntu to my disk. Current Vista runs on C:\ and XP on D:\. Partitions are divided with Vista having the first 52GB and XP having the remaining 100GB with a total of 160GB HDD. I dont use Vista very much but i dont want to delete the partition because its a pain in the *** to load back on. I use XP frequently because all my apps work with it. So i figured i would take about 12GB from the Vista partition and 15 from the XP partition. So i have about 27 GB of unallocated space between my Vista and XP partitions. I created a 2GB SWAP right after the Vista partition and the remaining 25GB to Ext3. Now after i install Ubuntu i want to reinstall the BCD bootloader. After thats done i can use EasyBCD to add the Grub bootloader to the BCD bootloader. But i still need Grub bootloader installed to do that. So my question is basically, should i format the swap and ext3 partition as logical or primary, or just one, or none. I need it so that Grub is at the beginning of the Ext3 partition, i think. Any help so i dont **** up my ****.

Heres how i have it setup currently.
[IMG]http://www.sgn.servegame.com/image/partitions.jpg[/IMG]

---

### Post by David Robertson on 2008-04-11
Some simple stuff about partitions that might help:
1. You get four primary partitions on a drive.
2. You can make on of these an extended partition and shove lots of logical drives into it.
I think the only restriction is you can't 'boot' a logical drive.

Using Vista to boot both XP and Linux will be fine. It would go better if Linux was at the end of the disk. XP may get confused and refuse to boot with the extra partitions in front of it. I think a warm install of XP will fix. You can probably directly edit XP's boot.ini or Vista's BCD but I don't have any experience in doing this (well not for slightly different partitions!)

The MBR (Master Boot Record) has enough information to load the partition table and kick start a partition. The partition sets up the main menus. It shouldn't matter which menu you see, they all should be able to boot the other.

GRUB may be packed into the MBR, but I would assume BCDEasy will pack it up and hide it inside Vista's file system.

I rekon you should get XP shoved up against Vista (as the second partition and as installed) and put Linux at the end of the Disk.

Hope this gives you more information and hope others also reply.

---

### Post by Herman on 2008-04-11
> So i figured i would take about 12GB from the Vista partition and 15 from the XP partition. So i have about 27 GB of unallocated space between my Vista and XP partitions. I created a 2GB SWAP right after the Vista partition and the remaining 25GB to Ext3.:) You only need 1 GB of swap area, max, any more than that is just a waste of hard disk space. You should resize it smaller and make a new ext3 partition, 26 GB. :)
 > Now after i install Ubuntu i want to reinstall the BCD bootloader. After thats done i can use EasyBCD to add the Grub bootloader to the BCD bootloader. But i still need Grub bootloader installed to do that.  :) You need to use the Ubuntu 'Alternate' installation CD if you want to be able to install GRUB to wherever you want. The 'Desktop' Live Ubuntu CD will install GRUB to MBR in whichever it thinks is your first hard disk, but then it's easy enough to re-install the Windows boot loader there if that's what you want. With the 'Alternate' CD you can choose where to install GRUB, to the boot sector, to a different hard disk, or to a floppy disk, or somewhere else. See my signature links for details. :)
> So my question is basically, should i format the swap and ext3 partition as logical or primary, or just one, or none. I need it so that Grub is at the beginning of the Ext3 partition, i think. Any help so i dont **** up my ****.:) Well, I don't think it matters too much. Ubuntu can boot in a primary or a logical partition, it is only Windows that can't boot in a logical partition, so it probably won't matter.
You can install GRUB in the boot sector of your ext3 partition during installation if you use the 'Alternate' CD or else you instll GRUB anywhere later any time you like from the Live CD from a terminal, with a GRUB shell. :)

Regards, Herman :)

EDIT: David Robertson makes a few good points, I agree that it could be a little better if you keep the two Windows installations together and make the Ubuntu partitions at the end of the disk instead of in the middle. That's just so you won't be 'painting yourself into a corner', (partition wise).
If you make the Ubuntu partitions after your XP partition, and make the swap area at the end of your disk logical, or both Ubuntu and the swap area logical, you will be keeping your options open for creating more partitions if you ever decide you want to.
It's up to you to decide whether that might be important to you or not.

---

### Post by speed3b on 2008-04-12
Thanks for all the help! 
I moved the partitions around like you recommened. I have my vista partition first, followed by xp, followed by linux swap, followed by the root folder /sda4.
I used the alternative CD and it worked great. When installing you get to the partition editor part, all i had to do was select the swap area and make sure it was going to use it as swap, i then selected my sda4 partition and set it as root /, and went back to my sda1 and put the bootable flag next to it. After it went though the rest of the install and when it got to the grub install it asked where i wanted grub to install at, so i did /sda4 and it installed it there. It detected my BCD bootloader and added it to the grub bootloader. I booted up into my xp partition and added the grub bootloader using easybcd. So now i have the BCD bootloader (Vista bootloader) as my default bootloader and it contains all my os installs. So if i select the ubuntu install it loads up the grub bootloader, and i can either select ubuntu or the BCD bootloader and go back to the BCD bootloader to select windows, or just going in a constant loop through the two bootloaders.

Thanks again for the help! Im glad i didnt mess up my installs and everything went as planed.

---

### Post by Herman on 2008-04-12
:) Hey, great! Congratulations on your successful and trouble-free installation.
I like having my boot loaders boot each other (in a loop) too, in case I change my mind before I finish booting. :)
EasyBCD is a good boot loader, and computerguru (the developer of EasyBCD) is a good guy.
I'm glad you're enjoying Ubuntu. 

Happy Ubuntuing,
Regards, Herman :)

---

