---
title: "Issues installing UBUNTU as OS"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by walker48 on 2010-01-20
Just need some help here. I downloaded the .iso file for ubuntu 9.10. I put it on a DVD-R and it seemed to work. If I try to boot from the CD-Rom drive it says invalid boot.ini file. I tried using a friends ubuntu disk that worked for him to do it instead and it says the same thing. So i decided to try to install ubuntu inside of windows but it installs it and says that it need to restart to complete installation. So i reset the computer and it does not complete the installation. Any ways around this cause i really would like to get ubuntu on my desktop. Any help would be greatly appreciated.

---

### Post by Sef on 2010-01-21
1) What are your system specs?

2) Instead of installing, go down to 'check disk for errors' or something similar.

---

### Post by darkod on 2010-01-21
> **walker48 said:**
> Just need some help here. I downloaded the .iso file for ubuntu 9.10. I put it on a DVD-R and it seemed to work. If I try to boot from the CD-Rom drive it says invalid boot.ini file. I tried using a friends ubuntu disk that worked for him to do it instead and it says the same thing. So i decided to try to install ubuntu inside of windows but it installs it and says that it need to restart to complete installation. So i reset the computer and it does not complete the installation. Any ways around this cause i really would like to get ubuntu on my desktop. Any help would be greatly appreciated.

A message about invalid boot.ini file has nothing to do with ubuntu and the ISO. boot.ini is used by windows XP, so I guess this is what you have. And according to you this message was there even before trying to install wubi.

If the boot.ini was messed up even before trying to install wubi it might be the reason why the install process didn't finish bcause it needs to modify boot.ini with entry for wubi.

If your computer can't boot even without the ubuntu disc in the optical drive, you could try restoring your XP bootloader with XP install cd and instructions from here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Also make sure you are trying to boot the CD first, because it sounds like it's looking in your HDD boot.ini file. Or somehow you have boot.ini on the CD/DVD you created but then it would be wrong procedure in creating the disc. You didn't try to somehow make it bootable yourself right? Just burn the ISO as image on the cd/dvd and that's all you need to do, it's a bootable image itself and the disc will be bootable.

---

### Post by walker48 on 2010-01-21
Well this computer was home built and has a pirated version of xp on it...is there a way to fix the boot.ini without the x pdisk? I dont have one, lol. Or is there a way to just completely wipe the hard drive and then use Ubuntu as the only OS?

System Specs:
AMD Athlon(tm) 64 Processor
3000+
2.00 GHz, 1.50 GB of RAM

---

### Post by darkod on 2010-01-21
> **walker48 said:**
> Well this computer was home built and has a pirated version of xp on it...is there a way to fix the boot.ini without the x pdisk? I dont have one, lol. Or is there a way to just completely wipe the hard drive and then use Ubuntu as the only OS?

System Specs:
AMD Athlon(tm) 64 Processor
3000+
2.00 GHz, 1.50 GB of RAM

It's very easy to wipe the hdd and use ubuntu as only OS, but according to you, you can't boot with the ubuntu cd.
Once you can boot with the cd or usb stick, just select Install Ubuntu and in step 4 use the "Erase and use whole disk" option. That will wipe it and set up ubuntu with standard configuration (root + swap partitions).
Of course, all data will be gone so copy everything you need first.

---

### Post by walker48 on 2010-01-22
Alrighty. This is where I am. The computer was given to me, so Im not the one who put the pirated OS on there. But anyways. The .iso file for Ubuntu is fine. I even had a friend come over and double check it for me. It seems like the pirated version of XP that is on my comp decided to take it over and took away any ability to change the boot stuff. My friend and I worked on it for a few hours yesterday, and still no luck. Anyone have Ideas of any other way to wipe the harddrive so that I dont have to go and buy a new one......Or if you have any ideas of how to bring back the master boot, it would be awsome.

---

### Post by ancianoman on 2010-01-22
try wiping it with Hiren's Boot CD which will also repair the MBR
and format your hard drive...

[http://www.hirensbootcd.net/](http://www.hirensbootcd.net/)

when done the Ubuntu program will do the rest

---

### Post by presence1960 on 2010-01-22
> **walker48 said:**
> Alrighty. This is where I am. The computer was given to me, so Im not the one who put the pirated OS on there. But anyways. The .iso file for Ubuntu is fine. I even had a friend come over and double check it for me. It seems like the pirated version of XP that is on my comp decided to take it over and took away any ability to change the boot stuff. My friend and I worked on it for a few hours yesterday, and still no luck. Anyone have Ideas of any other way to wipe the harddrive so that I dont have to go and buy a new one......Or if you have any ideas of how to bring back the master boot, it would be awsome.

Take the hard disk out and put it in another computer. Just don't set it up to be the disk that boots. Use that computer to format the entire hard disk.

**_Lesson: Stay away from pirated software!!! _**
There is almost always malware embedded within it. Do you think they like you so much that they want to help you bypass Microsoft? You almost always get more than you bargained for!

---

### Post by pirateghost on 2010-01-22
BIOS is preboot.  windows pirated or not, cannot control what your BIOS options are.  YOU are responsible for setting the CD/DVD to boot, not the boot.ini file on the harddrive.

i think you are missing a step here that requires you to change what it boots to first.

---

### Post by darkod on 2010-01-22
> **pirateghost said:**
> BIOS is preboot.  windows pirated or not, cannot control what your BIOS options are.  YOU are responsible for setting the CD/DVD to boot, not the boot.ini file on the harddrive.

i think you are missing a step here that requires you to change what it boots to first.

It's not that I am supporting pirated software, but I was thinking to write something along these lines. I can't really see why any sort of pirated software would prevent you from booting from cd. BIOS is handling that. Or at least it should.

Of course, pirated software might have components I'm not aware of. :) Otherwise it really sounds like a step from the OP is missing (not criticizing you).

---

