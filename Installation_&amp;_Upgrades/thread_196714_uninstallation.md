---
title: "uninstallation"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by rizzz on 2006-06-14
After installing Ubuntu, I wanted to erase it and try another type of Linux like Red Hat or Suse. So without knowing the consequences, I went into my windows operating system and deleted the partitions that holds the Linux system. Now everytime I reboot my computer an error message shows up. What should I do? Should I install Linux again?

Is there any way to erase Ubuntu completely from my hard drive without deleting the whole drive? 

Thank you to whoever helps

---

### Post by truNWA on 2006-06-14
If you have the ubuntu live cd you could use it to open Gparted and erase the partition

---

### Post by rizzz on 2006-06-14
How do I open Gparted?

---

### Post by OneL on 2006-06-14
Try this:  get your XP installation disk.  Boot off of it and when you get to the choice of install or recovery console, pick  reovery console by typing R.

You'll then be asked which copy of Windows you want to repair.  Assuming you only have one, the only choice will be 1.  Type that.  Then at the command prompt, type fixmbr.  

Even if Windows tells you that you will destroy the free world if if do this, type y.  Wait until your hard drive light goes off.  Then type exit, remove the XP disk and reboot.

If the computer gods smiled upon you, you should boot into XP.  IF not come back here, and we'll try to help.

---

### Post by catlett on 2006-06-14
[QUOTE=OneL]Try this:  get your XP installation disk.  Boot off of it and when you get to the choice of install or recovery console, pick  reovery console by typing R.

You'll then be asked which copy of Windows you want to repair.  Assuming you only have one, the only choice will be 1.  Type that.  Then at the command prompt, type fixmbr.  

Even if Windows tells you that you will destroy the free world if if do this, type y.  Wait until your hard drive light goes off.  Then type exit, remove the XP disk and reboot.

If the computer gods smiled upon you, you should boot into XP.  IF not come back here, and we'll try to help.[/QUOTE]
Just follow these instructions and you'll be fine. What you did was you erased grub. Grub is the bootloader. You can erase grub but you have to replace it with another bootloader. You didn't so you couldn't boot into your system. If you follow these instructions you'll install the windows boot loader and you will be able to boot into windows.
Also if you install fedora or suse to ubuntu's partition the new installation will reinstall grub and you will be able to boot into the new install or windows.

Just wanted you to know you didn't "destroy" or "ruin" anything. You just accidentally erased the boot manager. At the most what you did was an annoyance especially if you are looking to install another lionux distro because all distros will install a bootloader that will let you boot to it and windows

---

### Post by RRS on 2006-06-14
Just to clarify;
Yes, follow Onel's directions and you'll be fine.

However, you didn't erase Grub when you erased Ubuntu, you simply confused it. If it was set to boot Ubuntu rather then Windows by default, it will look for Ubuntu when you  boot up the computer and won't find it, so it does nothing.

Grub normally resides in the MBR and following Onel's directions will remove it so you'll be ready for your next OS installation.

Good luck with your next adventure.

---

### Post by catlett on 2006-06-15
> **RRS]Just to clarify said:**
> 

rrs you are wrong 

grub does not reside in the mbr. Only stage 1 resides in the mbr. The rest of grub that does the actual booting is in your boot folder on your ubuntu partition. That is why you get grub error 17. Grub started and went to ubnuntu's partition but couldn't find the rest of grub.
. You didn't touch the mbr, you erased ubuntu's partition. If grub was entirely on the mbr it would have worked. You would have seen the menu and have been able to boot to windows and only given an an error when it looked for ubuntu.
This is why people make boot partitions. So grub can be on it's own partition at the front of the drive and if you change other parts of your hard drive grub willl always be there on it's own partition.

This is also why if you open your boot folder in ubuntu you will see the grub folder. And if you open the grub folder you will see the 1.5 stages. Ubuntu's install does not use a boot partititonb. It puts grub stage 1 on the mbr abd keeps the rest of grub in the boot folder.

In case anyone wants to see how I know about grub, it's simple. There is a grub manual that explains the boot process.  I[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)
[QUOTE]10 GRUB image files

GRUB consists of several images: two essential stages, optional stages called Stage 1.5, one image for bootable CD-ROM, and two network boot images. Here is a short overview of them. See Internals, for more details.

stage1
    This is an essential image used for booting up GRUB. Usually, this is embedded in an MBR or the boot sector of a partition. Because a PC boot sector is 512 bytes, the size of this image is exactly 512 bytes.

    All stage1 must do is to load Stage 2 or Stage 1.5 from a local disk. Because of the size restriction, stage1 encodes the location of Stage 2 (or Stage 1.5) in a block list format, so it never understand any filesystem structure.
stage2
    This is the core image of GRUB. It does everything but booting up itself. Usually, this is put in a filesystem, but that is not required.
e2fs_stage1_5
fat_stage1_5
ffs_stage1_5
jfs_stage1_5
minix_stage1_5
reiserfs_stage1_5
vstafs_stage1_5
xfs_stage1_5
    These are called Stage 1.5, because they serve as a bridge between stage1 and stage2, that is to say, Stage 1.5 is loaded by Stage 1 and Stage 1.5 loads Stage 2. The difference between stage1 and *_stage1_5 is that the former doesn't understand any filesystem while the latter understands one filesystem (e.g. e2fs_stage1_5 understands ext2fs). So you can move the Stage 2 image to another location safely, even after GRUB has been installed.

    While Stage 2 cannot generally be embedded in a fixed area as the size is so large, Stage 1.5 can be installed into the area right after an MBR, or the boot loader area of a ReiserFS or a FFS. 

---

### Post by RRS on 2006-06-15
> rrs you are wrong
Wouldn't be the first time.

For various reasons I did a couple uninstalls in the begining of my Ubuntu "explorations" and the help sources I was using at the time provided my partial understanding of Grub. Thanks for the fuller version. I've bookmarked your link for further study.

When I first decided to try Linux last fall I somehow overlooked the existance of these forums till about a month after I'd been up and running with Breezy. Fortunately I've since corrected that oversite and appreciate all the knowledge I've gained here.

rizzz;
Sorry to sidetrack from your problem. Have you been successfull with your repair?

---

### Post by rizzz on 2006-06-15
oh sorry about my late response.

i haven't tried anything yet. i just reinstalled ubuntu so that i can at least get to one of the operating systems. i will go ahead and see if i can do what you guys have instructed. 

i will write again if i have any problems 

thanks for your help. i really, really appreciate it.

---

### Post by bigken on 2006-06-15
Hi the **fixmbr** is right  but then you type **fixboot** then **exit **and reboot if these dont work go back into repair console and type  **bootcfg /rebuild**  failing that try a repair install hope this helps ;)

---

### Post by rizzz on 2006-06-16
well i followed the instructions and everything went well.

but i don't have any way to check whether i have successfully changed the boot loader back to windows. 

I do have one more question however. How do I find out the administrator's password. In the instructions, it said to type "1" when being asked which windows to repair. when I did this it asked me for a the administrator's password. I typed in the password that I thought was right, but it didn't work. I skiped it however, by just pressing enter and I finally reached the command line. So I am just curious as to which password it was talking about. Is there any way to go in the command line and find out the password?

---

### Post by bigken on 2006-06-16
[QUOTE=rizzz]well i followed the instructions and everything went well.

but i don't have any way to check whether i have successfully changed the boot loader back to windows. 

I do have one more question however. How do I find out the administrator's password. In the instructions, it said to type "1" when being asked which windows to repair. when I did this it asked me for a the administrator's password. I typed in the password that I thought was right, but it didn't work. I skiped it however, by just pressing enter and I finally reached the command line. So I am just curious as to which password it was talking about. Is there any way to go in the command line and find out the password?[/QUOTE]


its the administrator password when you 1st install xp you are asked to insert a password or leave it blank ;)
so your your system dont have a admin password

---

### Post by bigken on 2006-06-16
please delete double post

---

