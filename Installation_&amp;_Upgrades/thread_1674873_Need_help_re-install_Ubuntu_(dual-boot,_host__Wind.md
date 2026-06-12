---
title: "Need help re-install Ubuntu (dual-boot, host : Windows XP)"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by emisoundsmachine on 2011-01-24
I need help re-installing Ubuntu 10.10 on my PC. Previously (first time installation), was from Ubuntu Desktop LiveCD using USB. I installed Ubuntu on different drive. I didn't make any swap-drive before (I just know about it). Also, I upgraded to Ubuntu Studio manually from terminal. 

It was my first time, and i did a quite little mess with my current  installation during the course of learning sudo and setting up for audio  related works.

The problem I have now,
1. No sound from the speaker (after replacing ALSA with OSS4, which was success, and trying to get back to ALSA, which was not)
2. I missed that speaker icon on default setting of Ubuntu Studio Desktop theme. It supposed to be on top-right of the panel. That icon also contains sub-menu to "Rhythmbox" and "Volume Setting".
3. I think i made a lot of sudo apt-get install and compiling from tar, i think i downloaded many unnecessary dependency files, which I'm not using it.
4. I downloaded and install complete Ubuntu Studio audio/video/graphic package. After trying all the stuff inside, I found out that i didn't need all of them. I decide to remove the package and just get necessary software that i need to use. However, I failed to remove the package using "sudo apt-get remove ubuntustudio-etc" I can't remember what i did during the course of sudo-ing things.

I just want a fresh new install of Ubuntu Desktop, and build from grown up again, and keep the Ubuntu Studio desktop theme on top of it.

I did made a little Google and find out about GParted and Super Grub Disk. What I had in mind is, 
1. boot to Gparted using USB, 
2. delete/clean the drive where I installed Ubuntu
3. reboot to Super Grub Disk from other USB, to fix mbr things,
4. reboot to Windows,
5. reformat the drive I've installed Ubuntu before
6. re-install fresh copy of Ubuntu again.

However I failed to boot to Gparted as per instruction on their website. I did try clicking the makeboot.bat from the USB while I was on Windows, and I still got boot error.
I don't know how to Gparted from Ubuntu. I had the Gparted package installed but  I get this line :```
 Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon
```If there is a better way to do this, rather than going through GParted and SGD to fix mbr, please guide me. 

Again, it was my first time on Ubuntu, I just want a fresh new install of Ubuntu Desktop, and build from grown  up again, and keep the Ubuntu Studio desktop theme on top of it.

Thanks.

---

### Post by presence1960 on 2011-01-24
Just go ahead and install the new Ubuntu over the previous install. The MBR will be taken care of during the install-GRUB will be written to the MBR. keep it simple please!

If you feel more comfortable formatting your ubuntu disk and creating an ext4 partition for Ubuntu and a swap partition you can do so by booting the Ubuntu Live Cd and choosing try ubuntu. When the desktop loads go System > Administration > Gparted Partition Editor. This will open gparted. After creating the partitions for Ubuntu install. When you get to the partitioning window of the installer choose Specify partitions manually to install to the partition you created.

The bootable gparted USB you made is meant to be booted, you can not execute the software by clicking on any file. Your computer BIOS must be able to boot from USB and you must set the BIOS to boot USB before hard disk.

If your BIOS is not able to boot from USB you will have to use a CD

---

### Post by emisoundsmachine on 2011-01-24
Thanks. I don't have CD. I failed to boot from USB. Is there any possibility I can boot from USB or using 3rd hard drive? Either from Windows or Ubuntu or my 3rd storage drive?

---

### Post by emisoundsmachine on 2011-01-25
I solved my problem. A fresh new install over previous install. Thanks for your guide.

---

### Post by Bucky Ball on 2011-01-25
Now, all you need is the ubuntustudio-audio packages available from the repositories (System>Admin>Administration>Synaptics Package Manager - search and install). You can also get artwork and if you're into video too, ubuntustudio-video.

If you want the works, ubuntustudio-desktop. You don't need to install Ubuntu Studio from an ISO image, but you probably already know that. ;)

---

