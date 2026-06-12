---
title: "Need help with dual boot; completely new at this"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Zinanni1986 on 2010-04-30
Hello,

First off, I wish to say that while I am completely new here at the forums, I am absolutely sure this has been covered in some thread in the past. Apologies in advance.

I just attained a copy of 10.04 and wish to dual boot it with Windows 7. I am not interested in using Wubi (I have done that for 9.10 and I want a "true dual boot" system). I am aware of the inevitability of screwing up my boot record for Windows 7, thus keeping me from booting windows up. All of the tutorials/tips/advice I have seen all suggest that I boot off of the installation disc for Windows 7.

My main problem is this; I bought my laptop with Windows 7 preloaded. I have no access to an installation disc whatsoever. Any advice on how I can get this done without "destroying" my copy of Windows?

My OS's are 32 bit btw. I dont know if that helps.

---

### Post by Zinanni1986 on 2010-04-30
anyone?

---

### Post by Zinanni1986 on 2010-04-30
bump....sorry but id like to get this resolved

---

### Post by marythecontrary on 2010-04-30
Here's a guide for making recovery disks in Windows 7: [http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Back anything up that you have after making the disks and then boot the computer with an Ubuntu disk in the CD drive. When I did it about a year ago, it partitioned the hard drive for me. I don't know if it still does.

---

### Post by limey_rick on 2010-04-30
Hi and welcome to the forums.

If you did not get installation disks with your PC because windows was pre loaded, normally you can create a set of disk to restore your PC to its factory settings; have you been able to do this?

If you cannot, you should first take a full backup of your PC. Next, download the Live CD for Ubuntu and boot it (set CD to boot from BIOS). IN the Live CD, go to the System->Administration menu and select GPArted. This will show you the disks on your PC. You need to find a place to install Ubuntu by either creating a partition on a blank disk area or resizing your Windows7 partition to make room. 

Once you have some free space, create two partitions, one a EXT4 partition and one a SWAP partition. The EXT4 partition should have a mount point of / or root, and the SWAP partition should be about 1,5 x memory size, you can install Ubuntu. 

See here for more info: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

If you have one disk, GRUB (bootloader) will install on the MBR of the disk, so that when you reboot, it will start GRUB and you will see the Ubuntu boot options. If you have more than one disk, you need to make sure GRUB installs on the first disk selected by the PC BIOS. 

In any case, when you reboot, if you don't see Windows7 as an option to select, do not panic. Bring up Ubuntu, run all updates 

System->Administration->Update Manager

and 

> sudo update-grub

This should find your windows parition and you will see it next time you start the PC.

If this does not work, then likely GRUB installed on the other disk (if you have more than one), so select this as first boot disk in the BIOS.

---

### Post by Zinanni1986 on 2010-04-30
Good news is I have recovery discs (my laptop is an Acer and I made recovery discs but usually when you recover with these, they will wipe everything clean and return the computer to the state of which it was in when I first took it out of the box). The Ubuntu disc will partition it for me but I know for sure it will overwrite (or mess up via some other method) my MBR for windows. I'm just trying to plan all of this out before I attempt this.



> **marythecontrary said:**
> Here's a guide for making recovery disks in Windows 7: [http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Back anything up that you have after making the disks and then boot the computer with an Ubuntu disk in the CD drive. When I did it about a year ago, it partitioned the hard drive for me. I don't know if it still does.

---

### Post by Yogotiss on 2010-04-30
> **Zinanni1986 said:**
> Hello,

First off, I wish to say that while I am completely new here at the forums, I am absolutely sure this has been covered in some thread in the past. Apologies in advance.

I just attained a copy of 10.04 and wish to dual boot it with Windows 7. I am not interested in using Wubi (I have done that for 9.10 and I want a "true dual boot" system). I am aware of the inevitability of screwing up my boot record for Windows 7, thus keeping me from booting windows up. All of the tutorials/tips/advice I have seen all suggest that I boot off of the installation disc for Windows 7.

My main problem is this; I bought my laptop with Windows 7 preloaded. I have no access to an installation disc whatsoever. Any advice on how I can get this done without "destroying" my copy of Windows?

My OS's are 32 bit btw. I dont know if that helps.

Normally most machine have a hidden partition that acts as installation disk. You can access it from a pre-configured hot key during boot. You also should be able to create your own (Recovery CDs) within Windows if that option is available. Now about your issue. If you don't want to use WUBI and want to do a "true" dual boot. You'll have to split your Windows 7 partition using various tools. For instance, I use Acronis and sometimes GParted. GParted may be your best bet because it is free and it is Linux based.

Note: Find out what hot key will restore your machine for the hidden partition in case of any mishaps and also back up any wanted data to a flash drive before hand.

---

### Post by Zinanni1986 on 2010-04-30
> **limey_rick said:**
> Hi and welcome to the forums.

If you did not get installation disks with your PC because windows was pre loaded, normally you can create a set of disk to restore your PC to its factory settings; have you been able to do this?

If you cannot, you should first take a full backup of your PC. Next, download the Live CD for Ubuntu and boot it (set CD to boot from BIOS). IN the Live CD, go to the System->Administration menu and select GPArted. This will show you the disks on your PC. You need to find a place to install Ubuntu by either creating a partition on a blank disk area or resizing your Windows7 partition to make room.


Ok I am currently backing my system up now (im creating a system image with my external HDD) and i do have recovery discs just in case. Quick question: so should i use GParted as opposed to the windows disk management tool to resize my partition?

---

### Post by Zinanni1986 on 2010-04-30
bump

---

### Post by limey_rick on 2010-04-30
I have not used the windows resize tool, only GParted. I don't think it will make any difference which one you use.

---

### Post by Zinanni1986 on 2010-04-30
Ok i cannot partition my hard drive beyone 1.9 gb because i think there is an unmovable file that disk defrag cannot take care of.....I'm not a big fan of Wubi so im giving up on dual booting

---

### Post by ctsbc on 2010-04-30
If you upgraded Ubuntu and Windows don't boot, take a look at this link: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector").

It's a simple solution that worked very well in my dual boot installation.

---

