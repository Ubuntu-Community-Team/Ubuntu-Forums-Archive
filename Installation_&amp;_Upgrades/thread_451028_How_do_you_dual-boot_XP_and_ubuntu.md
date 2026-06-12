---
title: "How do you dual-boot XP and ubuntu"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Gamaxray on 2007-05-21
Ok so i have read plenty of how tos and documentation on this and i understand the basics. and also this might help i have never installed a OS or dual-booted be for. and i have a 89GB hard drive with 56.2 GB free space so how other people partitioned  there hard drives.

---

### Post by mocqueanh on 2007-05-21
You have installed XP ?
OK, just boot from Ubuntu installion CD (press F11, Esc, Del,.........depend on your PC ) to choose the boot from menu.
Follow instructions, Ubuntu will give you some install option, choose the option to dual boot with Windows

---

### Post by tajmox on 2007-05-22
whenever i install windows after ubuntu this is what i have to do

1)  Boot from live cd

2) to into terminal

3) type sudo grub

4) type root (hd0,0)

5) type setup (hd0)

6) reboot and your grub is restored

This is assuming that your ubuntu partition is hda1 or sda1
If you get an error try root (hd0,1)

Once you are back in Ubuntu you will have to add windows manually to your /boot/grub/menu.lst
or use the grubconf tool

---

### Post by arvevans on 2007-05-22
GamaXray

On the assumption that you may have never done this before...here is the way I did it:

[LIST=1]
[*]Boot from the Linux CD (set your CMOS to select CDROM as the first boot device)
[*]Start the Linux Install process and go as far as to set up the DOS and Linux partitions and write them to disk.
[*]Now, go back to your MS-XP install CD and install MS-XP normally on the partition that you reserved for it with the Linux partitioner.
[*]At this point you can reboot with the Linux CD and do a full Linux install, including setting up GRUB to do the dual-boot thing.
[/LIST]

The reason for this somewhat complicated procedure is that you must establish partitions for Linux so that XP will not clobber them when it installs.  But, XP thinks it is the world's only operating system and will always overwrite any boot sector information that already exists.  For this reason you must actually install Linux after XP is installed so it will have an opportunity to re-build the MBR (Master Boot Record) pointer to do a dual boot.

No.  I don't run MS-XP on my computer.  This was for setting up a friend's business computer which required both MS-XP and Linux to support a proprietary software function that thus far refuses to run under WINE.

Arv
_._

---

### Post by siteguru on 2007-05-22
How I did it?

#1 Boot with LiveCD.
#2 Use Gnome Partition Editor (System > Administration menu) to resize the existing partition to give yourself, say, 10GB
#3 Follow the instructions it gives you - you may have to boot into windows and run a chkdsk so that the partition can be setup properly, then reboot twice. Once done, follow #1 and #2 again.
#4 Double-click on the Install icon and follow the instructions - select the option to install to the largest continuous free space.
#5 Let the install complete - it will create two new partitions, a large one as ext3 for the Ubuntu install, and a smaller one (about 500MB) as a swap.
#6 Remove the CD when prompted and allow PC to reboot.
#7 You should now see a Grub menu with Ubuntu as the first 2 options (the 2nd one is recovery mode) and your XP install should also be visible. (It was the 5th item in the list for me).
#8 If you need to change the default boot then open a terminal and **gksudo gedit /boot/grub/menu.lst** ... change the line **default	0** to **default	4** (in my case - the 5th item is number 4).

---

### Post by therezin on 2007-05-22
> #2 Use Gnome Partition Editor (System > Administration menu) to resize the existing partition to give yourself, say, 10GB

Will the gnome partition editor handle shrinking NTFS partitions? I've been having some major trouble using other partition editors, they either don't recognise my SATA drive or won't resize the partition...

---

### Post by siteguru on 2007-05-22
Worked fine for me. Recognises NTFS fine, and my HDD is a Seagate SATA 120GB. 8)

Only thing for me was step 3 (chkdsk) but after that all went sweet.

---

### Post by -=BINGO-BANGO=- on 2007-05-22
> **therezin said:**
> Will the gnome partition editor handle shrinking NTFS partitions? I've been having some major trouble using other partition editors, they either don't recognise my SATA drive or won't resize the partition...

Same think with me, do you get this type of error? [http://i19.tinypic.com/682tyr5.pngv]("http://i19.tinypic.com/682tyr5.pngv")

---

### Post by dan171717 on 2007-05-22
> **tajmox said:**
> whenever i install windows after ubuntu this is what i have to do

1)  Boot from live cd

2) to into terminal

3) type sudo grub

4) type root (hd0,0)

5) type setup (hd0)

6) reboot and your grub is restored

This is assuming that your ubuntu partition is hda1 or sda1
If you get an error try root (hd0,1)

Once you are back in Ubuntu you will have to add windows manually to your /boot/grub/menu.lst
or use the grubconf tool


u r trying to install kubuntu installing that i think is diffrent. dont use the installers partioners. if u have an xp cd then burn all your stuff you want to keeponto a cd or dvd then fdisk and wipe the drive then istall ubuntu and shrink it to about 50/50 or whatever then set the other blank partion to ntfs then install win and follow the instructions to install grub

---

### Post by siteguru on 2007-05-22
> **-=BINGO-BANGO=- said:**
> Same think with me, do you get this type of error? [http://i19.tinypic.com/682tyr5.pngv]("http://i19.tinypic.com/682tyr5.pngv")

Don't use the partitioner within the install process - do the partitioning via the LiveCD **before** you try to install.

---

### Post by Dennis the Menace on 2007-05-22
> **siteguru said:**
> How I did it?

#8 If you need to change the default boot then open a terminal and **gksudo gedit /boot/grub/menu.lst** ... change the line **default	0** to **default	4** (in my case - the 5th item is number 4).

Thanks for that last bit of Info, I've just dual booted with XP & Ubuntu, didn't know how to alter the boot sequence, your advice worked a treat, I'll be forever in your debt.

---

### Post by dan171717 on 2007-05-23
> **siteguru said:**
> Don't use the partitioner within the install process - do the partitioning via the LiveCD **before** you try to install. i said that! just clean the hdd but dont do it if you dont have an  xp cd!!

---

### Post by siteguru on 2007-05-23
I don't understand - who needs to clean the HDD? I just resized my HDD to create free space (I had to run chkdsk in Windows beforehand) and then used the Install to create the required partitions.

Maybe we're saying the same thing but that's not how I read it. :S

---

### Post by rickycodie on 2007-05-31
this is a great how to but it does not include this step.

[http://ubuntuforums.org/showthread.php?t=456819](http://ubuntuforums.org/showthread.php?t=456819)

---

