---
title: "No root file system is defined.   (Wubi 9.1)"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by rajeshk4u on 2009-12-26
Hello,
 
I installed Ubuntu 9.10 through the Windows XP Desktop (Wubi). It created a 17GB Ubuntu disk file in Windows.
 
When I rebooted the PC, I got the option of booting into XP or Ubuntu. 
 
Pop-up message comes up saying "**checking installation..**." and another pop-up with message "**No root file system is defined. Please correct this from the partition menu**". I can't exit and go into operating system to investigate. [COLOR=red]**How do I fix this??**[/COLOR]
 
I can run Ubuntu from the live CD, but I cannot boot up from disk. I am able to browse my Windows drive through the live CD and explore Windows files. 
 
I really don't know why I am getting this error. The only thing perculiar in my system is that I have an Asus A8V Deluxe motherboard, which as a built-in Promise SATA RAID controller. Although, I have a SINGLE Hard Disk. (In the BIOS it is set to RAID mode, it I put to IDE mode, Windows refuses to see the disk and I get a blue screen).
 
There are other standard SATA/PATA ports which are not used at all.
 
I have used the live CD to get this information about my system (GParted):
 
/dev/sda1 - fat32 - recovery 4.4GB - hidden, lba
/dev/sda2 - ntfs - windows 185GB - boot
 
I don't want to loose my Windows partition and want to use in Wubi. 
 
Also, how do I access the 17GB Ubuntu disk which is sitting under Windows?.

---

### Post by phillw on 2009-12-26
> **rajeshk4u said:**
> Hello,
 
I installed Ubuntu 9.10 through the Windows XP Desktop (Wubi). It created a 17GB Ubuntu disk file in Windows.
 
When I rebooted the PC, I got the option of booting into XP or Ubuntu. 
 
Pop-up message comes up saying "**checking installation..**." and another pop-up with message "**No root file system is defined. Please correct this from the partition menu**". I can't exit and go into operating system to investigate. [COLOR=red]**How do I fix this??**[/COLOR]
 
I can run Ubuntu from the live CD, but I cannot boot up from disk. I am able to browse my Windows drive through the live CD and explore Windows files. 
 
I really don't know why I am getting this error. The only thing perculiar in my system is that I have an Asus A8V Deluxe motherboard, which as a built-in Promise SATA RAID controller. Although, I have a SINGLE Hard Disk. (In the BIOS it is set to RAID mode, it I put to IDE mode, Windows refuses to see the disk and I get a blue screen).
 
There are other standard SATA/PATA ports which are not used at all.
 
I have used the live CD to get this information about my system (GParted):
 
/dev/sda1 - fat32 - recovery 4.4GB - hidden, lba
/dev/sda2 - ntfs - windows 185GB - boot
 
I don't want to loose my Windows partition and want to use in Wubi. 
 
Also, how do I access the 17GB Ubuntu disk which is sitting under Windows?.

Hi, and welcome to the forum,

If your MoBo and Win are thinking that a single disk is in RAID, then we could be in a bit of bother here. For a start, I doubt that you have a 200GB hard disk - I'd expect more on a modern machine.

Now, we can't blame everyone here, the latest ubuntu has 'issues' with some raid set ups. What worries me more, however, is that Win cannot 'see' itself when you disable RAID which really means that ubuntu doesn't really stand a chance.

That, to me, would be the first point of working out why you are having a problem.

Don't use Gparted on your hard disk. It cannot see the whole disk.

1) Beg, steal or borrow an external hard drive
2) Backup your data (documents / videos / music) from your windows installation
3) Re install your Win with IDE mode turned **on**.

Others may have a work-around, but, IMHO on a one disk system, you do not need, nor want RAID. How Win and your BIOS have gotten themselves to install just puts up too many variables.

If you'd like to have a 'play' with Ubuntu before you sort out your hard disk, then I'd suggest using a USB memory stick with persistence - persitence means it will save changes that you make, unlike running off the LiveCD.

Your MoBo should support USB booting if it has RAID support.

For how to make a usb with persistence, head over here --> [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

Regards,

Phill.

---

### Post by rajeshk4u on 2009-12-26
Thanks....
 
1. The disk is about 200Gb (it is an older machine - AMD Athlon64).
 
2. I am not convinced that Ubuntu can't see the RAID disk. I say this because, when I boot from the Ubuntu Live CD it has no problem in seeing my Windows directory and I can explore Windows file system. 
 
3. I also tried the second approach. Booting from the Ubuntu Live CD and I can choose boot from 'primary disk' again it was able to boot from this disk (but I got the error No root file system is defined...).
 
4. I think not seeing the RAID disk is a (partly) a red herring, as Ubuntu does BOOT UP and I can see the ORANGE background. So it is reading the disk and booting etc... It just gets stuck in the installation process... and this error message 'No roof file system is defined....'
 
I feel it is a matter of a tweak... but I just don't know what I need to do.....

---

### Post by phillw on 2009-12-26
If you installed ubuntu **within** windows, then you have Wubi.

To recover a Wubi Install it is

>  				 				**Re: sh:grub > desperation** 			
 			 			 		   		 		 		[SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

 	Quote:
 	 	 		 			 				# Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 			 		 	 	 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
 		                   		  		  		 		 			 				__________________
				[GRUB2]("https://help.ubuntu.com/community/Grub2") : [G2-Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") [G2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[G2-Tasks]("http://ubuntuforums.org/showthread.php?t=1302743") [DiskSpace]("http://help.ubuntu.com/community/RecoverLostDiskSpace")  
[Expand /]("http://ubuntuforums.org/showthread.php?t=1219270") [SUM]("http://ubuntuforums.org/showthread.php?t=818177") 			
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 4 Weeks Ago at 06:24 PM.. 					 					 				* 			


If you installed a true 'dual boot' - i.e. you had seperate partitions, then it would be different. as your output of your hard disk does not show a unbuntu area, then I can only surmise that you went the Wubi route. Post back if you think that is wrong.

Phill.

---

### Post by rajeshk4u on 2009-12-26
I took the Wubi root.

---

### Post by phillw on 2009-12-26
> **rajeshk4u said:**
> I took the Wubi root.

that one, I posted above should sort it. I don't run Wubi, but this is the thread with it on [http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page=7](http://www.uluga.ubuntuforums.org/showthread.php?t=1314064&page=7)

Don't go back in the thread, as that is before we had a solution, if that How-To doesn't sort you, carry on reading through the thread.

Just be aware that, for whatever reason, updates within Wubi seem to break it each time. Yes, it is not good & not a good advertisement for Ubuntu. If you can spare 10GB of hard disk space, put a **real** ubuntu intallation on. You & it will be much happier together, honest.

Phill.

---

