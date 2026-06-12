---
title: "Use windows boot manager?"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by jeremyleroy96 on 2010-04-14
Hi i am currently installing ubuntu on my main PC. I need to dual boot because i am a gamer but i don't game a lot so i figured well i need to dual boot :D. So can i use the windows boot loader? its more easy for my family then GRUB.

---

### Post by rtilson on 2010-04-14
I have used be windows boot loader when using XP to dual boot. When it comes to Vista and Win7 there are programs that claim to allow you to set up the windows boot loader to dual boot. They have never worked for me. They usually mess up my boot loader and have to reinstall it which is a pain to do.

GRUB on the hand has been good and never had a problem with it. I dont see how windows boot loader is easier to use over GRUB.

---

### Post by jeremyleroy96 on 2010-04-14
well the problem is when i installed it i said don't install boot loader so ummm.... 

grub shows up all those recovery modes and is just two complicated for my parents but i understand it. I just need the windows boot loader!

---

### Post by longbeard on 2010-04-15
Would be interested in learning how to do this with NTLDR on Windows XP! - I installed Ubuntu but it just wouldn't run because GRUB or whatever bootloader doesn't function or wasn't installed as promised. I've seen similar complaints but no solution offered.

I found one file "ntldr" in C:\WINDOWS\SoftwareDistribution\Download\<some hex number>. It doesn't appear to be an executable. I couldn't find anything in C:\ nor could I find "boot.ini". 

Interesting I found "boot.ini.backup" in C:\WINDOWS\pss with following content:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer

---

### Post by ottosykora on 2010-04-15
well yes, it is possible, the setup is kind of manual work, but then it works fine, at leats so I experinced on XP.
The actual boot loader for the linux has to be installed in the boot partition of the linux then.
There are number of howtos in net: look here [http://icculus.org/~lucasw/Linux/Linux%20and%20XP%20Bootloading.html](http://icculus.org/~lucasw/Linux/Linux%20and%20XP%20Bootloading.html)

or 
[http://www.wellho.net/solutions/general-linux-and-xp-loading-a-dual-boot-system.html](http://www.wellho.net/solutions/general-linux-and-xp-loading-a-dual-boot-system.html)

---

### Post by dc_wmj2 on 2010-05-27
I have the same question - I wanna dual boot ubuntu with the XP-Bootmanager.

I copied the Ubuntu MBR (extended Partition, ext4) to a file in c:\ (NTFS,primary,first partition) and made an entry in boot.ini

I got the same result as the guy who is writing in link no 1: After XP-Boot-Loader, the (Lilo) boot-manager shows up and when doing a choice, the system freezes (directly after printing the line "Loading Ubuntu"). 

Is there any solution? I searched already on the net. There was nothing helpfully in the tutorials.

---

