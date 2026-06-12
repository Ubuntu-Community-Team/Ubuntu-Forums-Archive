---
title: "install grub on acer l'top, not in windows mbr"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by steve33 on 2008-03-19
hi, 

i wish to install ubuntu 6.10 alongside windows xp on an acer 3662WLMI laptop;and avoidiing installation of grub on the current mbr in order to keep the acer D2D recovery system in place. 

On ubunutu 7.04 there is the option to install grub on a partition when using manual setup by clicking on 'advanced';version  6.10 doesn't appear to have the option at the similar point of the setup.I will usethe current third partion for the install incl swap fille, i  would appreciate any advice to avoid overwirting the curent mr wth grub for the install. Many thanks

---

### Post by Jimmey on 2008-03-19
Grub usually detects any recovery partitions and adds them to it's default menu.lst as a selectable option when you boot the computer.

However, the best way to avoid overwriting the MBR would be to not install GRUB at all during the boot process.

Once the system is installed, boot into a liveCD, set the grub root to your ubuntu partition, E.G. ```
sudo grub 
``` then ```
root (hd0,0)
``` (depending on which partition your Ubuntu is installed to) and installing the grub files into a removable media, like a floppy, a CD or a USB stick. Then setting the BIOS to boot from that device should be enough to display a GRUB menu - Whenever that device isn't present, the normal Windows bootloader will load.

---

### Post by logos34 on 2008-03-19
Get the text-based **alternate** install 6.10 cd--it has grub bootloader options at the end of the installation.  Use either the **/dev/sda3** format (assuming you put root on the third partition and swap on the fourth), or use '(hd0,**2**)'.  And then you can use windows bootloader to boot ubuntu or like Jimmey said above put grub on a grub boot floppy or cd.  You could also use supergrub cd.

---

### Post by steve33 on 2008-03-20
thanks; i have loaded 6.10 on a previous acer  l'top and the recov
 partition didn't appear in the startup menu,& the acer d2d recovery process Alt + F10 no longer worked - the recov p'tition is hidden which i guess you realise. 

when you say to install grub on the ubuntu partition once system is installed would that not rewrite the mbr as said above?

when typing root hd0,0 does the last 0 refer to the partition number ubuntu is installed

thanks, Steve

---

### Post by Herman on 2008-03-20
:) Hello steve33,
My wife and I have an Acer laptop each and I just recently installed Ubuntu in another Acer laptop for a friend of mine who is sick and tired of having to have Windows re-installed because of viruses and malware.

I didn't know anything about the Acer D2D thing. it must be something relatively new. I do know that I have run the Acer eRecovery program in my wife's computer after she let someone borrow her computer and they booted Windows XP and got it infected.
Normally she only uses Ubuntu but Windows XP is still there. 
We don't really care about XP, but I remember running the Acer eRecovery, I think I just booted it up from [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), I can't remember for sure now, it was a while ago. Anyway, it worked fine and I was surprised it didn't even delete Ubuntu.

I looked up D2D recovery in google and ironically, I found this link where it is suggested to install Linux as a way to repair the Acer D2D Recovery system, [How To Repair The Acer D2D Recovery]("http://ezinearticles.com/?How-to-Repair-the-Acer-D2D-Recovery&id=794500").

> when typing root hd0,0 does the last 0 refer to the partition number ubuntu is installedNo, you are supposed to know what partitions you have in your computer and if youdon't, you should check first either by running 'sudo fdisk -lu' or by looking with Gnome Partition Editor, (System-->Administration-->Partition Editor), (in the Live CD, you may need to install it if you're using a hard disk installed Ubuntu system).
Normally, (hd0) will be the MBR of your first hard drive, and (hd1) will be the MBR of hard disk number 2, and so on.
Partitions will be (hd0,0) for partition number 1, (hd0,1) for partition number 2, and (hd0,2) for partition number 3, and so on.
[Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System").

You can make a backup of any hard disk's MBR before working with boot loaders or programs that install boot loaders, here is a link, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").

There are lots of other ways to replace the IPL for Windows in your MBR and overwrite GRUB's stage1, here is a link, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

If you need to fix a boot sector (first sector of a partition), if it's FAT32 you can restore it from your backup boot sector with Linux's 'sudo dosfsck -ar /dev/hda1'
```
sudo dosfsck -ar /dev/hda1
```Where: 'dev/hda1' is your FAT32 partition that needs the boot sector replaced.
[When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup").
The eRecovery partition in my Acer laptop is FAT32, I imagine a D2D recovery partition would be also?

It you have an NTFS file system and you need to replace the boot sector with it's backup, I don't know the Linux command for that at the moment, but the backup boot sector for an NTFS partitioon is in the last sector of the partition. I imagine if all else failed a Linux 'dd command' would work.

Nothing is to be feared, only to be understood.

Regards, Herman :)

---

### Post by steve33 on 2008-03-21
thanks for the excellent help with links etc; I will back up the mbr this time!,my partitions are NTFS,not sure if pqservice is but will find out; can i ask if you use wireless using the Acer built-in card?the wireless on my previous acer2303 laptop wouldn't work,so will shelve out for a compatible card if I have no joy again ! Thanks, Steve

---

### Post by Herman on 2008-03-21
> thanks for the excellent help with links etc; I will back up the mbr this time!,my partitions are NTFS,not sure if pqservice is but will find out;If your P2P partition is NTFS and you need to restore the boot sector from it's backup you can do that with TestDisk, [12 NTFS Boot sector recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery").
TestDisk is a program that can be installed in Ubuntu or in a Ubuntu Live CD (in a LiveCD it will only last for one session though).
The [Ubuntu Rescue Remix Live CD]("http://ubuntu-rescue-remix.org/") contains TestDisk.


About wireless network card support, yes I am using the built in card.
 I haven't bothered looking into that so far with Gutsy or Hardy, but I wrote about my experience with that in Ubuntu Fiesty Fawn here, [Setting up my Acer Aspire Notebook for Wireless Networking in Ubuntu]("http://users.bigpond.net.au/hermanzone/p11.htm#wireless_network_configuration").

Something I will need to look into very soon is how to use the new 3G wireless Bigpond Broadband access cards with an Acer laptop, because that's one of the requirements for my friend who I installed Ubuntu for.
I was very pleased with Linux's support for GPS data, which is another thing that is important for my friend.
Linux, and especially Ubuntu, is getting better and better all the time. Sometimes it takes a little bit of work to set things up, but other things turn out a lot easier than expected and work a lot better in Linux, once you know your way around.

Regards, Herman :)

---

