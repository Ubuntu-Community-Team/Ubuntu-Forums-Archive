---
title: "How do i reinstall Win98"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Fxy on 2007-10-25
Hi, a while ago i installed ubuntu over Windows 98 :) on an old Tiny computer in my bedroom.  Once installed i found that the computer didn't have alot of free memory so ubuntu ran & still runs at like 1mps taking forever to load folders and programs etc:(.  What i want to know is how can i reinstall Windows:confused::confused::confused:.  ATM im trying to install Win NT using 3 floppies provded but im havin no luck:(:mad::(.

---

### Post by kast on 2007-10-25
Well you would need the 98 CD , Windows 98 would be like 50 floppies!

there are other flavors of Linux out there that could  run on your older pc allot better then Ubuntu, Did you install Ubuntu? you can try a less graphical intense version like Xbuntu, i run that on my server.

I would Google search for Linux Distributions on old hardware

* Damn Small Linux - a very popular low-resource Linux, based on Debian and Knoppix. Runs on a 486 in a graphical mode,

* DeLi Linux - this is a real pearl. DeLi stands for “Desktop Light” Linux. It is capable of running on a 386 computer in a graphical mode! Lately, version 0.7 has been released. Certainly worth trying on some very old PCs.
 
* Zenwalk - minimal requirements for Zenwalk are: Pentium III, 128 Mb RAM and 2Gb HDD. However, it can be run pretty fine on PII, as well. Zenwalk is a modern Linux distro for low-resource PC-s.

Good luck!

---

### Post by Fxy on 2007-10-25
> **kast said:**
> Well you would need the 98 CD , Windows 98 would be like 50 floppies!
 
there are other flavors of Linux out there that could run on your older pc allot better then Ubuntu, Did you install Ubuntu? you can try a less graphical intense version like Xbuntu, i run that on my server.
 
I would Google search for Linux Distributions on old hardware
 
* Damn Small Linux - a very popular low-resource Linux, based on Debian and Knoppix. Runs on a 486 in a graphical mode,
 
* DeLi Linux - this is a real pearl. DeLi stands for &#8220;Desktop Light&#8221; Linux. It is capable of running on a 386 computer in a graphical mode! Lately, version 0.7 has been released. Certainly worth trying on some very old PCs.
 
* Zenwalk - minimal requirements for Zenwalk are: Pentium III, 128 Mb RAM and 2Gb HDD. However, it can be run pretty fine on PII, as well. Zenwalk is a modern Linux distro for low-resource PC-s.
 
Good luck!
 
 
Yes ive got ubuntu installed & it was installed using the txt installer & is currently running on bare minimum. I orignally had Windows 98 installed before ubuntu but am now currently trying to install Windows NT over ubuntu. I downloaded win NT from some bootdisk site & it can be installed using only 3 floppies.

---

### Post by kast on 2007-10-25
Hummm.. i don't believe you can fit NT on 3 floppies, but good luck with it. I would recommend trying another flavor on Linux, one that would run a little better on a low end pc, like Damn Small Linux, or even try Xbuntu

---

### Post by maybeway36 on 2007-10-25
If you need to get rid of GRUB after installing Windows, boot a DOS boot floppy and type:
```
fdisk /mbr
```

---

### Post by Fxy on 2007-10-26
> **maybeway36 said:**
> If you need to get rid of GRUB after installing Windows, boot a DOS boot floppy and type:
```
fdisk /mbr
```
 
Yes but how can i reinstall windows first, thats more my problem @ the moment...:confused::confused::confused:

---

### Post by Golem XIV on 2007-10-26
> **Fxy said:**
> Yes ive got ubuntu installed & it was installed using the txt installer & is currently running on bare minimum. I orignally had Windows 98 installed before ubuntu but am now currently trying to install Windows NT over ubuntu. I downloaded win NT from some bootdisk site & it can be installed using only 3 floppies.

Those three diskettes are only to prepare the system for a Windows NT install.  You *will* need the Windows NT CD also, or at least the installation files (there are several hundred MB of those; you can copy them over to, say, C:\i386).  The diskettes are there only if your system is not able to boot from CD or if you have the Windows NT installation files copied previously.

I did a lot of this several years back, when NT was new and CD ROM drives were expensive :-)

---

### Post by Fxy on 2007-10-26
Right ok... Then how do i reinstall windows 98 :confused::confused::confused: using a cd ive got, caz before there was an option on start-up when i hit escape or when a floppy was inserted, now all i get r some ubuntu start-up options:confused::confused::confused:...

---

### Post by kast on 2007-10-26
If your BIOS is enabled to boot from your CDROM (assuming you have one?) then you should be able to boot directly to a 98 cd, and reinstall.

 What exactly is it not doing? Do you have a CDROM? have you enabled the option in your BIOS to boot from your CDROM?]

 More info would be helpful

---

### Post by Eddie Wilson on 2007-10-26
Windows 98 needs to install from a dos prompt. Go to the boot disk site that you got the NT disk from and download the startup disk for win 98 or win me. You have to boot your computer from the floppy, pick enable cdrom support, and at the dos prompt, cd to the cdrom drive and start the setup program. Thats how I've always done it.
Eddie

---

### Post by kast on 2007-10-26
Eddie thats right! damn its been along time, just used to freaking XP i guess

---

### Post by maybeway36 on 2007-10-26
I have the OEM CD and it boots from CD. But its always nice to have a DOS/Win9x boot floppy on hand anyways.

---

### Post by Eddie Wilson on 2007-10-26
Sounds like he doesn't have an OEM cd. Also I don't know because I don't believe he stated but he will have to reformat his hard drive if he installed using the full hd. I still think he should try DSL, Puppy or something like that.
Eddie

---

### Post by Fxy on 2007-10-28
Well when the computer is switched on it will load ubuntu, or on the other hand if i press Esc or F12 it will only load ubuntu options:confused:... The 3 floppies i had for win nt did have the full os on them caz ive installed nt on another computer:KS...

---

### Post by Fxy on 2007-11-16
maybeway how do u get the cd to run, caz if i insert it when the computer starts up nothin happens it just normally starts ubuntu...

---

