---
title: "help booting ubuntu with unusual configuration"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by entropyjones on 2007-08-26
Ok so I'm trying to install Ubuntu 6.06 lts. I want to dual boot it with winXP. Should I use the latest version of ubuntu? I figured since I am newbie I should stick with the fully supported version but who knows. 

My computer has three hard drives. 1 is SATA, and the other two are IDE. They are on the secondary IDE channel. The primary IDE has two CDROM drives. It just ended up that way because I never dreamed of needing my extra IDE channels when I set the machine up but then ended up adding more and more hd's.

I have ubuntu installed on the 2nd IDE master. So in the linuxverse that should be HD3 right for the IDE's? I think this is important but I'll explain why when I get into grub.

So about grub.. I installed grub for windows on the SATA drive where my windows XP installation is.

This seems to have gone ok and I now get a menu that says,

Microsoft windows XP
Grub

At boot up.

However selecting grub just gives me the boot loader. 

When I find /vmlinuz from the grub shell I get 

h2,0 as the location.

Trying to do anything with HD2 returns various error messages however. 

I tried the command /kernel /vmlinuz root=/dev/hd2 vga=ext

which got me

error 17 cannot mount selected partition

I'm not sure how to configure grub to make it line up with my hooky configuration and make it find my ubuntu installation. Should there be a menu.1st file visible in my windows installation in the \boot directory that grub for windows has you create? 

Anybody got any ideas? Yes I know I should have ubuntu on the SATA drive and relegate windows XP to the curb however I'm a gamer. I want to get into open source operating systems but I'm not giving up my video games to do it. I installed RHEL at work and configured SMB so I'm not completely clueless but the RHEL install was on a computer with a single HD which has become completely devoted to linux and nothing else.

I learned dos/windows back in the old days by trying to make games work and I think I can learn a lot about linux from wine and making games work under it. But that's a project. I don't want to give up games in the meantime!

---

### Post by zach12 on 2007-08-26
you need to set your bios to boot from cd and then just start up your computer and from ther it just hiting yes or no

---

### Post by dulbirakan on 2007-08-26
> **entropyjones said:**
> Ok so I'm trying to install Ubuntu 6.06 lts. I want to dual boot it with winXP. Should I use the latest version of ubuntu? I figured since I am newbie I should stick with the fully supported version but who knows. 

As far as I know fully supported version only matters if you paid for support services. Use the latest release, each release is better than the previous IMHO.

> **entropyjones said:**
>  So about grub.. I installed grub for windows on the SATA drive where my windows XP installation is.

This seems to have gone ok and I now get a menu that says,

Microsoft windows XP
Grub 

I think you messed up grub and are using windows boot ini together with it. It would have been better to just use grub.

> **entropyjones said:**
>  They are on the secondary IDE channel ......... I have ubuntu installed on the 2nd IDE master. So in the linuxverse that should be HD3 right for the IDE's? 

Seems fair enough.

> **entropyjones said:**
>   

h2,0 as the location.



if what you said above about hd3 is right why are you trying to mount HD2 which was the optical drive. This seems to be the problem.

> **entropyjones said:**
>   Anybody got any ideas? Yes I know I should have ubuntu on the SATA drive and relegate windows XP to the curb however I'm a gamer. I want to get into open source operating systems but I'm not giving up my video games to do it. I installed RHEL at work and configured SMB so I'm not completely clueless but the RHEL install was on a computer with a single HD which has become completely devoted to linux and nothing else.

I learned dos/windows back in the old days by trying to make games work and I think I can learn a lot about linux from wine and making games work under it. But that's a project. I don't want to give up games in the meantime!


Nope, You do not need ubuntu on sata but you should not have messed up grub. It should work fine with default values installed. I also reccomend considering Linux games some of them are really nice.

---

### Post by louieb on 2007-08-26
Just as a matter of common practice base on what works: Place both your CD drives on one IDE channnel and your two hard drives on the other. Double check your master/slave jumper setings for the drives. (the drive pluged into the end connector should be jumpered to Master. Mixing IDE and SATA drives can sometimes confuse GRUB.
you say you tried ```
root=/dev/hd2 vga=ext
``` 
Well /dev/hd2 is la la land, there is no such place. 
 
At this point 1st take a look at the dual boot and psychocats links in my signature. Lots of good install stuff on both sites. 2nd I'd make the changes to the drive hookup described above and reinstall Ubuntu. 
 
Like I mentioned earlier SATA, IDE, and Linux installs sometimes dont work out of the box. You may wind up having to make an adjustment to the /boot/grub/device.map. If you try the stuff I metioned above and it still doen't work Then get back and I will give you some other stuff to try.

---

### Post by entropyjones on 2007-08-26
Is there a way to see what drives are available from the grub shell? I've read that you can't actually mount a volume from grub is that true?

The grub I'm using isn't exactly broken it's grub for windows. It's installed on the sata drive with my windows xp installation. Your right that the boot.ini file has been modified though. By these instructions from the grub for windows install.txt file. Sorry in advance for text spam.

INSTALL:
--------

	you need to compile these files under CYGWIN
	get GRUB, for example in the directory /usr/local/src/grub-0.93
	install these files in grub-0.93/ntfsboot
	run "make" in the ntfsboot directory


Usage:
------

1) get a compiled stage1 and stage2 image and put these in C:\boot
   for example compiled on a linux machine

2) add the following line to the file C:\boot.ini

   C:\boot\stage1="GRUB"

   you may need to do 

	   ATTRIB -R -H -S C:\boot.ini

   to make the file visible and writable and 

	   ATTRIB +R +H +S C:\boot.ini

   to revert the attributes of the file

3) run grubinstall
   This will update the embedded blocklists in the files stage1 and stage2

   You should rerun this utility after moving/changing the files stage1 
   or stage2 and after running tools like defragmentation

   grubinstall [-d device] [-1 stage1] [-2 stage2] [-m menu] [-l] [-a]
   grubinstall [-s] [-1 stage1] [-2 stage2] [-m menu] [-l] [-a]
   grubinstall [-b] [-1 stage1] [-2 stage2]
   grubinstall [-i file] [-1 stage1] [-2 stage2]
       -d C:                  : partition where the files are
       -d (hd0,0)             : partition where the files are
       -1 C:\boot\stage1      : boot sector
       -2 C:\boot\stage2      : secondary boot loader
       -m /boot/menu.lst      : grub boot menu
       -l                     : force LBA mode
       -b                     : make boot floppy
       -i boot.img            : make boot disk image
       -s                     : scan partitions
       -a                     : alternate grub partition name for menu

       device can be a disk or GRUB partition identifier 
       stage1 and stage2 must be paths to win32 file names
 
   The defaults are such that if you put the files in C:\boot
   you can simply go for "grubinstall"

4) uninstall
   just delete the C:\boot directory, and remove the entry from C:\boot.ini
   as described in 1). No registry entries were used by using the tool.



Any more ideas?

---

### Post by logos34 on 2007-08-26
You mean you're using WinGrub, right?  Or the grldr and menu.lst in the grub4dos package? My own humble opinion is that the former is needlessly difficult to configure.  The latter works much better. 

The above posters have some good points and I agree that **you should try to use Grub boot loader**.  It should be possible to get it to work without a great deal of effort even in your mixed  sata-pata/ide system.

Would you want to try installing grub on the sata, your boot disk?

---

### Post by entropyjones on 2007-08-26
I'm not against using grub to boot windows at all. I just read some conflicting information about it.

Specifically that grub didn't support ntfs and also something about not installing it into your mbr.

---

### Post by logos34 on 2007-08-26
Grub overwrites the windows bootloader on the MBR...some people don't want that, but it doesn't hurt anything (In fact grub is superior because it has multiboot capability).  You can also install grub on the bootsector of the linux root (or boot) partition.  But the MBR is usually fine.  It can't directly boot windows, it chainloads it.  It boots linux directly.

Tiy might want to read the [Grub Page]("http://www.psychocats.net/ubuntu/mountwindows").  It should dispell any lingering unease about Grub.

Do you have the dapper live cd or the alternate?  If the former, can you get an internet connection running it?  If so you might want to run this in a terminal and post it:

**sudo fdisk -l **(lowercase L)

Just to nail down the facts (you have a few disks).

---

### Post by dulbirakan on 2007-08-27
> **logos34 said:**
> Grub overwrites the windows bootloader on the MBR...some people don't want that, but it doesn't hurt anything (In fact grub is superior because it has multiboot capability).  You can also install grub on the bootsector of the linux root (or boot) partition.  But the MBR is usually fine.  It can't directly boot windows, it chainloads it.  It boots linux directly.

Tiy might want to read the [Grub Page]("http://www.psychocats.net/ubuntu/mountwindows").  It should dispell any lingering unease about Grub.

Do you have the dapper live cd or the alternate?  If the former, can you get an internet connection running it?  If so you might want to run this in a terminal and post it:

**sudo fdisk -l **(lowercase L)

Just to nail down the facts (you have a few disks).

Nicely done...

---

### Post by st0n3cutt3r on 2007-09-01
.

---

