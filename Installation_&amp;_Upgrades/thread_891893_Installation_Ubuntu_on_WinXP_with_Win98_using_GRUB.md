---
title: "Installation Ubuntu on WinXP with Win98 using GRUB"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by spbook on 2008-08-16
Hello,

I am new to to Ubuntu, so I came first with installation question.

I have a WinXP machine dual booting WIN98 using GRUB.
I have the IDE master NTFS disk with WINXP, slave IDE FAT32 disk with WIN98 and have decided to put another slave ID disk to the system entirely dedicated to Ubuntu.
I am using XP boot loader 
to chose default XP system or WIN98 boot at startup and already using GRUB for fooling WIN98 slave disk into primary so that WIN98 boots from slave IDE.

I have a UBUNTU install CD 8.04 LTS.

My question is what is the recommended procedure to install UBUNTU on such a system. 

Thanks for help.

---

### Post by Herman on 2008-08-16
> I have a WinXP machine dual booting WIN98 using GRUB.:) Okay, I am assuming then that you already have a 'Dedicated GRUB Partition'. Just install Ubuntu in the new hard disk and install GRUB either to the boot sector of Ubuntu's own partition or else to the Master Boot Record of the hard disk you are installing Ubuntu in.

You are able to choose where to install GRUB in step 7 of 7 in the Desktop CD's installer, see figure 20 in the following link, [COLOR=#000000][Hardy Heron LTS / Windows XP Dual Boot Installation A]("http://www.herman.linuxmaniac.net/p24.html")[/COLOR] (you will need to scroll down to about 1/4 of the way up from the bottom of the page).

Then when you are booting and you see your normal GRUB menu, (from your GRUB in your Dedicted GRUB partition installed to MBR in your first hard disk), press your 'c' key for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and do a [Chainloader Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot").
For example I am guessing maybe it would be something like this,
```
root (hd2)
chainloader +1
boot
```That should boot the MBR in your third hard disk, so if you installed Ubuntu's GRUB to MBR in  your third hard disk, then your existiing GRUB will hand over the control of the booting to Ubuntu's GRUB here and you can boot Ubuntu.

After you boot Ubuntu, just mount your Dedicated GRUB Partition and add the same chainloader command you just used to your /boot/grub/menu.lst file. It's easy to mount other file systems in Ubuntu Hardy Heron, [Click-Icon Mounting]("http://users.bigpond.net.au/hermanzone/p10.htm#Click-Icon_Mounting").

A copy of the output from 'sudo fdisk -lu' command is often useful when discussing booting issues and other issues too, so if you have problems please include a copy of that so someone can help you better. One fdisk output is worth a thousand words.  :)

Regards, Herman :)

---

### Post by Herman on 2008-08-16
[Super Grub Disk]("http://www.supergrubdisk.org/")
If you make yourself a Super Grub CD or USB or something, you might find that useful in case you're not good at running GRUB from the command line.

---

### Post by spbook on 2008-08-16
So, if I understood right, I can pull out all disks, install
Ubuntu clean on the dedicated disk, and then reverse disk to slave and putting all disks back, and then configuring GRUB chainload. 

Thanks for now, I will try.

---

### Post by Herman on 2008-08-16
Well you can do it that way if you don't mind going to all the work of opening up your computer case and unplugging the other hard disks. 
It shouldn't be necessary to go to that extreme though, but if you feel like doing it that way it will work okay. :)

---

