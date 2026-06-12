---
title: "Questions about installing multiple distros"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by timzak on 2007-06-26
Before I step out to install some other distros on my system, I had a couple of questions:

1) Can multiple distros share the same swap partition, so that I don't have to create a swap for each distro I install on the same computer?

2) How do you go about managing grub?  Some distros use Lilo instead of Grub.  Should distros be installed in a certain order so that you don't overwrite your boot manager?

Thanks in advance.

---

### Post by SoggyCornflake on 2007-06-26
> **timzak said:**
> 
1) Can multiple distros share the same swap partition, so that I don't have to create a swap for each distro I install on the same computer?
.
Yes.   

> **timzak said:**
> 2) How do you go about managing grub?  Some distros use Lilo instead of Grub.  Should distros be installed in a certain order so that you don't overwrite your boot manager?  

Thanks in advance.
I prefer Grub to Lilo.   I don't think it matters which Linux Distro you load first.

You may need to do some manual editing of Grub.  It's not that hard.  :D If you plan on having a Microsoft OS, you'll need to install that one first - or you'll probably be re installing whatever you loaded first.

---

### Post by Herman on 2007-06-26
Hello timzak
I agree with SoggyCornflake, you can use GRUB or LiLo or GAG Boot Manager, whichever you like.

[GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")  How to use GNU/GRUB, the                                               GRand Unified Bootloader             
[LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html")                      LiLo the Linux Loader Page, about installing LiLo in Ubuntu and booting             
[GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")  GAG Boot Manager, a Windows and Linux booting alternative

If you use GRUB in the MBR, you can boot other Linux distros that have GRUB in them by using the 'configfile' command to bring up their GRUB menus. If the other Linux distro uses LiLo, you can install that to the first sector of the operating system's partition and then 'chainload' it with GRUB. 
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Or use GAG Boot Manager because it's 'operating system independant' and being graphical, is quick and easy to change around when you change operating systems.

Enjoy your multi booting,
Regards, Herman :D

---

### Post by timzak on 2007-06-26
Thanks, guys!  :p

Do you have to do anything special to get each distro to see the swap partition?  In other words, must you manually go into each distro and tell it where the swap partition is, or does it find it and use it automatically?

---

### Post by dabl on 2007-06-26
> **timzak said:**
> Do you have to do anything special to get each distro to see the swap partition? 

Nope, "Linux swap" is a standard type of partition.  I have 4 OS's installed on 3 hard drives, and the 3 Linuces all use the same swap space (one at a time, of course).  Kubuntu 32-bit, Ubuntu 64-bit, and elive.  No problem.

On Grub, you need to remember "Last Linux wins".  In other words, each time you install a Linux OS, it will write a boot menu (for all OS's it finds on the system) by default, unless you direct it otherwise.  For my setup, I just let them write over the boot menu, and then after the last one was installed (Ubuntu), I edited that menu.lst file to show the names of the kernels, and to put Kubuntu and elive below the "Automagic" line in the menu.lst, along with Win XP, so they wouldn't be changed by Ubuntu kernel upgrades.  :)

---

### Post by Rmac57 on 2007-08-17
Have 2 distros (Dapper LTS hd1 & Server 6.06 hd2) and 2 hd's.
Question 1: Can I run dapper and see the servers files so I can config in a GUI rather than command line?

Question 2: Server is LAMP. How do I get new password on MySQL? Have triedthe following:
root@Ubuntu-LAMP: /usr# sudo mysqladmin - u root -p {here I inserted a password of choice}
This is what came back:
mysqlaadmin:conect to server at 'localhost' failed
error: 'Access denied for user 'root' @'localhost' (using password:YES)

This is first time I am setting up mysql server. 

Am real noob @ linux so be kind! 

Want to be able to run lamp server as fileserver and webserver 

Thanx in advance!

---

### Post by A-Sylum on 2007-08-17
well from what i can grasp your server is denying access from user root so is there an allow list you have to use or something? i dont know im not a server guy just trying to help :D.

---

