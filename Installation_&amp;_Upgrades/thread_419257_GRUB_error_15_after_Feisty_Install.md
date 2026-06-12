---
title: "GRUB error 15 after Feisty Install"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Soli Deo gloria on 2007-04-22
After installing Feisty and rebooting the computer I get:

[INDENT]GRUB Loading stage 1.5
GRUB Loading, please wait...
Error 15
[/INDENT]

My system is a IBM Netvista with a P4, 1GB RAM and 200GB IDE HD. I manually partitioned the disk in 190GB for / and 10GB for swap. I used JFS for /.

Here is the tail of my /boot/grub/menu.lst :

[INDENT]title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6bff1f1-84e9-42c2-9053-acb5daa4123c ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e6bff1f1-84e9-42c2-9053-acb5daa4123c ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
[/INDENT]


And here is my /etc/fstab :

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e6bff1f1-84e9-42c2-9053-acb5daa4123c /               jfs     defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=110e6993-723c-42ab-9ff7-88d010cfb7c5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
[/INDENT]


Have tried a couple of things but without success up to know.
PLEASE HELP.

_______
Marco

---

### Post by Soli Deo gloria on 2007-04-23
Help Please!!!!!!!!!!!!!!

---

### Post by ukemike on 2007-04-23
I'm having the same problem on the same type of Pc.  Mine is a Netvista X40 or X41 (I think).  It was IBMs answer to the imac where the computer is integrated into the back of the lcd screen.

Anyway, the first time I installed it seemed to have worked except I couldn't log on with the account name and password I had entered at the start of the install.  When I rebooted I got the Grub error 15 and it would stop there.   Now on two consecutive re-attempts to install each time the computer has frozen most of the way through the install and on reboot I get the same grub error.   I'm beginning to think the HD has bad sectors or something, which would be odd since the HD is only about 2 years old.

---

### Post by yeleek on 2007-04-23
Before you pack it in - look at this [http://ubuntuforums.org/showthread.php?t=417447&page=4](http://ubuntuforums.org/showthread.php?t=417447&page=4)

I've been having huge problems with installing Fiesty all over the weekend.  Lots of different grub errors.  Just followed that pendrive install (make it 750 not 700 tho) and its worked fine.

So now wondering if the problem is grub after all.

---

### Post by Soli Deo gloria on 2007-04-23
Hmm, just opened the computer and discovered that the disk was indeed a PATA one and not an IDE as reported by BIOS.
Don't know if it changes anything ...

---

### Post by zvacet on 2007-04-23
> 15 : File not found
This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

For example, if you get this error during booting, maybe Grub is telling you it can't find the specified kernel or initrd.img file. Usually this is because of a mistake in editing your menu.lst file, for example, the exact path or name of your kernel or initrd.img contains an error or a typo.
Super Grub can boot your operating system by symlinks to the kernel if you use, from the Main Menu,--> Boot Gnu/Linux and  Other OSes --> Boot Gnu/Linux -->...
Boot with Super Grub Disk instead, and then with your operating system running you can check your file and correct your menu entry for Linux.
Open your menu.lst file with 'sudo gedit /boot/grub/menu.lst', if you are using Ubuntu Linux.
Use the command 'ls /boot' to check for the correct name for your Linux kernel and initrd.img.
Copy the correct name from the terminal output to the text file and paste it to avoid typos. Don't forget to save the changes in your menu.lst file before your close it.

This error can also occur if the files needed to boot with are missing or corrupt in the /boot/grub directory. Refer to Grub loading stage1.5 for how to completley delete possibly corrupted grub files and restore them again from /sbin/grub.

i hope this will help you.

---

### Post by Soli Deo gloria on 2007-04-23
Found the problem and it had nothing to do with Ubuntu.
BIOS was reporting a different size for the harddisk.
Just downloaded a BIOS update and tada!!! Feisty booted very nicely.
I am glad it was not Ubuntu related.
Thanks for all the help and God bless.

________
Marco

---

