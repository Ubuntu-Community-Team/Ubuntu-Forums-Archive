---
title: "Failed Ubuntu and XP dualboot"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by elaintarha on 2006-10-03
I KNEW IT!

I am a Windows user. I have to use UX at work frequently so I also know about that side. However I've stayed off Linux because the installation hasnt been as straightforward as Windows (maybe because I'm used to Windows installations). Then I saw this Ubuntu: it looks good and simple to use, I tried the Ubuntu on CD and I liked it. 

So, I read few topics: "I have XP and want to install Ubuntu as dualboot", etc, "just install it, it will nicely do the partitions for you. NO it didnt

I had: 
200gb HD with 
- 20GB partition (C: XP installed) 
and 
- 180GB partition (D: storage drive)

I added 80GB drive as E for Ubuntu. 

I started Ubuntu from CD, clicked install, selected "format (etc) and install on the 80GB drive". Installation proceeded. 

*Reboot* -> startup menu:

1. Ubuntu -> worked OK
2. some other ubuntu stuff
3. some other ubuntu stuff
4. Windows XP -> "Cannot start, missing <system drive>\system32\hal.dll, please reinstall it"

Of course I won't install hal.dll, I just reinstalled XP (partitioned 10GB from 180GB partition for XP):
- now the original C: drive (20GB with XP in it) is (D:\) and unusable "do you want to format it"
- The 180GB storage is C:, cannot be changed to "because it is part of a boot partition

Of course the Ubuntu installation is lost.

I hope someday these damned installations would just work for normal mortal people. It is not up to us to understand that shite, it should just WORK.

timo

---

### Post by jimbren on 2006-10-03
Dual booting and getting different OSs to play nicely together is frustrating.  The linux world tries to help becuase it has to--how else do we get people to try it?  The MS world doesn't think they have to and they don't.  Every new version of windows comes with new dual boot challenges.

My recommendation:
1) backup whatever data (pictures, docs, mp3s, etc) is in the 180GB partition.  if there are any program, forget about 'em and resign yourself to reinstalling them.  If you already have a good backup (and you *do*, right?)

Wipe the 200GB drive completely and install Windows on it, all as a single drive.  Don't bother updating windows or installing software at this point.

Install ubuntu again on the 80GB drive, verify you can get into both operating systems.

Now use Ubuntu for a week exclusively and ask yourself if you *really* need windows.

my .02

---

### Post by cotcot on 2006-10-03
I am not sure you can blame ubuntu for the dll error. Obviously it is a known problem with an error in the boot.ini file of XP. 

Have a look on : [http://www.kellys-korner-xp.com/xp_haldll_missing.htm]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm")

It is an example with your error in a XP and Windows 2000 dual boot.

---

### Post by elaintarha on 2006-10-04
> **jimbren said:**
> Dual booting and getting different OSs to play nicely together is frustrating.  The linux world tries to help becuase it has to--how else do we get people to try it?  The MS world doesn't think they have to and they don't.  Every new version of windows comes with new dual boot challenges.

My recommendation:
1) backup whatever data (pictures, docs, mp3s, etc) is in the 180GB partition.  if there are any program, forget about 'em and resign yourself to reinstalling them.  If you already have a good backup (and you *do*, right?)

Wipe the 200GB drive completely and install Windows on it, all as a single drive.  Don't bother updating windows or installing software at this point.

Install ubuntu again on the 80GB drive, verify you can get into both operating systems.

Now use Ubuntu for a week exclusively and ask yourself if you *really* need windows.

my .02

Thats correct, most people, including myself, don't want to bother about too much configging to get it working, that's why i was hoping to get it done easily. 

You suggestion to reinstall everything is probably the best idea. I use computer at home mainly for internet and games, Linux only provides half of this that's why its difficult to find any use for it. Im sure I would be using Linux if the games would work on it. I am certain there are loads of people who would as well. 

thanks,
timo

---

### Post by elaintarha on 2006-10-04
> **cotcot said:**
> I am not sure you can blame ubuntu for the dll error. Obviously it is a known problem with an error in the boot.ini file of XP. 

Have a look on : [http://www.kellys-korner-xp.com/xp_haldll_missing.htm]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm")

It is an example with your error in a XP and Windows 2000 dual boot.

Thanks for link. Only thing I'm complaining about Ubuntu is that I was hoping everything would go smoothly. I am aware I cant really blame anything, I'm just hoping less fuss with these installations. Sometimes I wonder why they are so goddamn difficult to master.

---

