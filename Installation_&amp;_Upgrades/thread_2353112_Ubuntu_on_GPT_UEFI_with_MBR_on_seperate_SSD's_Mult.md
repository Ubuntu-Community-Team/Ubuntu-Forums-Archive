---
title: "Ubuntu on GPT UEFI with MBR on seperate SSD's Multi-Boot XP to 10 and Linux ??"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by klund12 on 2017-02-19
Hi,
Just upgrades MB to Z270 motherboard!

I had a multi boot MBR setup that would boot to grup(ver ?) on one drive (disk 1?). From there I could go to Unbuntu, or to a Win MBR boot menu (Disk?). There I could go to any native OS from XP to Win10. Very cool set up.

With the new motherboard, I have those same drives, but I now boot from a M.2, RAID 0, UEFI, GPT drive to UEFI installed Win 10 x64. The other drives are not showing in the BIOS as boot available drives.  

I would like to know how to reinstall Unbuntu (if needed), to where it was before, but so that grup is first in control. From there I can go the new Win 10 install, or go to my old MBR boot menu on the old drive as it still is sitting there. 

It sounds like I know a lot about this. But NO I Do Not. I know something about this, but nothing about the details of actually doing it. I am a Total novice about command line linux stuff. It took a lot to figure out, with a lot of forum questions, how to install Ubuntu is my previous setup.

From what I've read so far, I think it should be possible to do what I want to do. But I have no idea How To Do It with out screwing things up. I could use a lot of hand holding with this. please. 
I have attached a snip of my drive set up as shown from Acronis 12 Disk Director. Unbuntu (latest version) sits at the end of disk 1. I think the system original booted to grup there. But I'm not totally sure. I think the MBR boot menu is on Disk 2 so I could get to XP to old Win10 (on Disk 2)
Also I need some translation from Win disk/partition names to linux;  Win Disk 1/XP-MCE 2005 = ????, etc, please help with a list  (ps Disk 1 & 2 are SSD's)
The system currently boots from Disk 5.
Yes I have a complete back up of everything. I have nothing on the Linux install that needs to be saved, if a reinstall is the easiest way to proceed. 

If some one with some major knowledge about these things could spell out the steps involved in my quest I would be most appreciative !!!

If you need more info to set up a procedure, please ask.

 MANY, MANY, MANY Thanks
KLund1

---

### Post by yancek on 2017-02-19
Mixing MBR installs which you have on the first four drives with EFI installs which you have on disk five is going to result in problems.  An EFI install has boot files in the EFI partition which is shown on that disk.  If you look in the directories in that partition, I expect you will see only files for windows 10 on that disk so you won't be able to boot any other OS this way.

If you look in the /boot/grub/grub.cfg file on Ubuntu, do you see entries for the other operating systems on disks 1-4?  You should and if you don't, you can run:  sudo update-grub which should pick them up.

The only way I 'think' you might be able to boot is to have your BIOS set to UEFI option when you want to boot windows 10 on disk 5 and change it manually to Legacy/CSM in the BIOS when you want to boot anything else.  If you want windows to use GPT, my understanding is that you 'must' use UEFI.  You can use GPT from an MBR install with Ubuntu or pretty much any Linux system.

You might take a look at the Ubuntu documentation at the site below discussing UEFI/MBR installs and dual booting.  There is a link on that page to 'boot repair' which it might be useful to download and run.  It has an option to Create BootInfo Summary and selecting that will give you a link which you can post here.  Doing that will give more detailed information on your system and someone may have an idea of how it might work, or not.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-02-19
You can also convert drives from MBR to gpt. I have not done it, but supposed it works.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 


I started using gpt with Ubuntu with 10.10. When Windows 8 came out with UEFI as standard, I knew eventually I would get a UEFI system, so I started in 2012 adding the ESP - efi system partition as first partition and bios_grub as second partition to all new or reformatted drives. And I use gpt on large flash drives.

But when you install Ubuntu in UEFI boot mode, it only installs to the ESP on drive seen as sda. If sda does not have ESP, then grub fails to install.
You may be able to move gpt drive to sda, by changing it to SATA0.

But are you booting in UEFI mode? Your disk2 looks like Windows 7 & Windows 10 in BIOS boot mode?

UEFI & BIOS are not compatible. Or once you start booting in one mode, you cannot switch. Or at grub menu you can only boot other systems in the same boot mode as you have booted into grub. You should always be able to multiple boot from UEFI boot menu, which some prefer, f10 or f12 key.

---

