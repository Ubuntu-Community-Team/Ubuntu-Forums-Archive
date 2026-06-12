---
title: "Dual boot (Ubuntu/Win.7) boots on windows 7 only"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by hervel56 on 2014-11-17
Hi all,

So I partitioned my disk to allow to install ubuntu.
I installed Ubuntu after having Windows 7 installed, as I understood it is the way to boot on GRUB which will give you the option to then boot with Windows or Ubuntu.
However, the computer will only boot on Windows 7 without having the option to select Ubuntu :-(

How can I fix that ?
Attached is a screenshot of Gparted. My laptop is a sony Y series, it has a very simple bios menu which allows me to boot on either the internal disk or external disk or network.
I expected I could choose which partition of the internal disk I could boot with.
I installed Ubuntu with the installation manager (the clean way I assume) on the Ubuntu live on the pendrive. I added a 2GB swap partition. However, the swap partition appears in Gparted as unallocated and with an unknown file system. That could be where the problem is.
It also created a 1.05MB partition lol. God knows why...
Last thing, the partition which hosts all the Ubuntu related partitions is an extended parition. If I tried to make it a primary partition, I get an error message saying I can only have 4 primary partitions. And so I couldn't create the swap partition (and the 1.05MB partition lol) as I already reach the limit of 4 primary.
If that is where the problem is, then I technically cannot have a second OS installed... which would suck quite bad. unless I remove the 100 MB "system reserved" windows partition which does not seem to be of any use. (correct me if I am wrong).

---

### Post by yancek on 2014-11-17
Being unable to boot Ubuntu after installing it usually is because its bootloader was not installed properly.  I would not delete the System Reserved partition (sda2) as that is most likely the windows boot partition.  Your windows system is sda3, sda4 is the Extended partition and inside the Extended partition is the Ubuntu install on sda5 and sda6 was probably meant to be the swap but shows as unknown for some reason.  You also have a 1MB unallocated space there.  You don't need to have the Ubuntu partition as primary, any Linux system will boot from a logical partition although windows will only do that if its boot files are on a primary partition. 

I'd suggest trying to reinstall Grub to the master boot record, /dev/sda.

---

### Post by oldfred on 2014-11-17
If you chose encrypted /home during install, then it is normal that gparted or other tools do not see the swap partition as it also is encrypted. 

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by hervel56 on 2014-11-19
thanks! 
so i reinstalled ubuntu following the same process (from the USB live version).
this time i didn't tick the "encrypt" box. (why would they give this option if that makes the OSfail to boot ? anyway...)
Now the swap partition is well labeled as swap and not as unknown, which is good I assume.
However the problem is the same :-(

When i start the computer it boots on windows 7. I installed Ubuntu after, as I read GRUB would give you the option of which OS you want to boot on. But I don't have the option.
So what could possibly be wrong ?
Do I have to manually change the mount points for windows when I am in gparted ?
Does the boot loader have to be mounted in a specific boot loader partition (just like with windows) or can it be mounted where you install the OS ? (Icouldn't find the anwer to that on the net)

Gparted now shows that Ubuntu is mounted at "/target", although i selected "/" as the mount point. Another mystery of linux I suppose.
Anyway, I'm not sure that is what prevents Ubuntu from booting at startup

---

### Post by yancek on 2014-11-19
The default on an Ubuntu install should be to install part of the Grub code to the master boot record of the first drive pointing to the partition on which you installed Ubuntu.  It creates a boot menu file (grub.cfg) and that usually contains a menuentry for any operating system found.  So if all you get is windows, something went wrong or the default was not accepted.  

You don't need to do anything with windows partitions.  You don't need a separate boot partition.  You could run the bootrepair script and post the output, information at the link below and this might give enough information for someone to point out the problem.  You should be able to download and run it from the installation medium or you could download on windows and create a bootable CD.

---

