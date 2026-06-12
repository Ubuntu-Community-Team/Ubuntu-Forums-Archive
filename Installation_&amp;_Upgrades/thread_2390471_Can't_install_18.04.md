---
title: "Can't install 18.04"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by hilario_ferreira on 2018-04-29
I have a problem with the installation of new 18.04.
I tried first an upgrade from 17.10.
It didn't work and I don't know the reason. Now I'm trying to install using an USB. Everything goes fine during installation, but when I restart the pc to run the new installed system it freezes when the logo "Ubuntu" is showing
Don't know what to do. I tried several times the installation but allways with same result. 

Can someone please help me.?

Please note that my previous installation of ubuntu 17.10 was in dual boot with windows 10.Now neither windows nor Ubuntu.

---

### Post by TheFu on 2018-04-29
What hardware?  Anything in the release notes that could be at issue like nVidia GPU?

Update 
or 
wipe and fresh install?

---

### Post by hilario_ferreira on 2018-04-29
My pc is a desktop machine.Motherboard Asrock !!!

How do I wipe disk ???

---

### Post by lb96179 on 2018-04-29
On installation, choose 'Erase ... and install' (... might be disk or existing os). Obviously, you'll want to have made a copy of any data you need first because it's not coming back after that.
Maybe a little more detail on the hardware, e.g. which mother board, cpu, graphics card, what ssd / hdd's, wifi etc.?
Good luck.

---

### Post by oldfred on 2018-04-29
What video card? 

UEFI or BIOS install? How you boot install media, is then how it installs.
And then is UEFI set to boot in that mode?

Did you change drive ports? Asmedia cause issues.
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)
 Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6) 


 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by s9032g@comcast.net on 2018-04-30
I have been with Ubuntu since 8.04. If you have an installation problem the simplest way to solve it is to backup what you need, wipe what you have, and do a clean install. Exactly how you wipe depends on whether you have a hard drive or an SSD. You can find free wipe programs using Google. Avoid complex solutions involving multiple commands. The simple way is best.

---

### Post by hilario_ferreira on 2018-04-30
I think the problem is really Ubuntu 18.04.
I reinstalled previous vers. 17.10, and everything went fine. Will try to upgrade from 17.10 maybe it's a good solution.
Thank you all.

---

### Post by Hodor on 2018-05-02
I doubt the problem is 18.04 per se - just did a clean install on an ASRock z97 Extreme 6, done and dusted in less than 10 minutes without a hitch. I would recommend a clean install - the upgrade option is nearly always a false friend, causes more problems than it solves.
Good luck

---

### Post by s9032g@comcast.net on 2018-05-03
I did the upgrade option from 17.10 (fully updated) to 18.04 LTS without a hitch.

---

### Post by nooneelse on 2018-05-03
> **hilario_ferreira said:**
> I have a problem with the installation of new 18.04.
I tried first an upgrade from 17.10.
It didn't work and I don't know the reason. Now I'm trying to install using an USB. Everything goes fine during installation, but when I restart the pc to run the new installed system it freezes when the logo "Ubuntu" is showing
Don't know what to do. I tried several times the installation but allways with same result. 

Can someone please help me.?

Please note that my previous installation of ubuntu 17.10 was in dual boot with windows 10.Now neither windows nor Ubuntu.

I think I know what can be your problem. I have the same issue too, the problem was with the video card (yeah boy, linux and video card issue, what a new)

To fix that BEFORE pressing enter to "Try ubuntu without installin" , press F6 (Other options) and choose the mode NOMODESET

I think this must work for you, if not, try other settings at F6

---

### Post by oldfred on 2018-05-03
The f6 is correct for BIOS boot only with purple screen.
If using UEFI with grub menu,  you have to manually edit grub linux line and replace quiet splash with nomodeset.
       
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

