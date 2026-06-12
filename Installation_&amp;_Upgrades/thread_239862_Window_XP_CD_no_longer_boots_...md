---
title: "Window XP CD no longer boots .."
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by Rez. on 2006-08-19
Hi again and yes, This is a question about XP :neutral: 
  I started a thread yesterday which you can read [here]("http://ubuntuforums.org/showthread.php?t=239157") about my experiences with trying to get Ubuntu to use the XP bootloader. After my third try today I finally gave up but my MBR was so screwed I had to do a 'Fixmbr' from the XP recovery console. 
 
 So I go through the usual routine of slipping in my XP disc and booting from it. I get the *'Press any key now to boot CD'* message and do just that. The DVD drives led lights up and for a brief second I get the familliar '*Setup is inspecting your computers hardware'* Message and then - **BOOM!**. Nada. A blank screen and the DVD drive spins down and the led shuts off.
 You're thinking it's a hardware problem right? It isn't. I can boot the ubuntu linux CD, SysrescCD and Windows 2000 install CD. No problems at all. Anything to do with XP hangs. I have an original XP Pro CD, Several Unattended CDs and a backup copy of my XP CD. All of them display exactly the same erratic behaviour.
 So why do I think this is an Ubuntu isuue? Well this only began to occur after my repeated installs of Ubuntu began. Also, Searches on google, MSN, Yahoo and ask yielded little to no results but I did find someone at [this]("http://www.linuxforums.org/forum/suse-linux-help/60730-can-no-longer-boot-xp-cd.html") Linux forum who was having the same problems.

Can anyone point me in the right direction here? My XP installs are only good for so long before a reinstall is neccessary and I need it despite my like for Ubuntu.
 Any help would be appreciated ..
 Thanks for reading.

 ](*,)  ](*,)  ](*,)

---

### Post by K.Mandla on 2006-08-20
I don't know that this is related, but I know I've had problems installing and over-installing OS's on one another without completely blanking the drive first.

In some cases I get leftover bootloaders and other crud mixed up, and as a result an entire installation gets hosed.

I don't know that it's an option for you, especially if you've got data on that drive that you want to keep, but [KillDisk ]("http://www.killdisk.com")is one of my favorites. You could wipe the disk completely and start over with a new XP install. 

Drastic, but an idea. Hope it helps.

---

### Post by Rez. on 2006-08-20
I did some more searching around last night and came across some interesting info. You guys are all correct that I was hasty thinking it wasn't totally a hardware problem. I came across this last night [link]("http://www.911cd.net/forums/lofiversion/index.php/t7658.html") which lead to this [link]("http://ce.aut.ac.ir/~naderan/WinXP.htm") and it's all pointing to either a hardware conflict or perhaps the computer is underpowered. I recently had to swap out my power supply for a lower rated one and it's powering an AMD64 proccessor and motherboard.
So, i guess it's up to me to see where the hardware is failing ... Thanks for the replies


For anyone with the same problem, Here's what I found.

[An explanation of what's going on and a possible soloution]("http://ce.aut.ac.ir/~naderan/WinXP.htm")

Thanks again.

---

### Post by randell6564 on 2006-08-20
> **Rez. said:**
> Hi again and yes, This is a question about XP :neutral: 
  I started a thread yesterday which you can read [here]("http://ubuntuforums.org/showthread.php?t=239157") about my experiences with trying to get Ubuntu to use the XP bootloader. After my third try today I finally gave up but my MBR was so screwed I had to do a 'Fixmbr' from the XP recovery console. 
 
 So I go through the usual routine of slipping in my XP disc and booting from it. I get the *'Press any key now to boot CD'* message and do just that. The DVD drives led lights up and for a brief second I get the familliar '*Setup is inspecting your computers hardware'* Message and then - **BOOM!**. Nada. A blank screen and the DVD drive spins down and the led shuts off.
 You're thinking it's a hardware problem right? It isn't. I can boot the ubuntu linux CD, SysrescCD and Windows 2000 install CD. No problems at all. Anything to do with XP hangs. I have an original XP Pro CD, Several Unattended CDs and a backup copy of my XP CD. All of them display exactly the same erratic behaviour.
 So why do I think this is an Ubuntu isuue? Well this only began to occur after my repeated installs of Ubuntu began. Also, Searches on google, MSN, Yahoo and ask yielded little to no results but I did find someone at [this]("http://www.linuxforums.org/forum/suse-linux-help/60730-can-no-longer-boot-xp-cd.html") Linux forum who was having the same problems.

Can anyone point me in the right direction here? My XP installs are only good for so long before a reinstall is neccessary and I need it despite my like for Ubuntu.
 Any help would be appreciated ..
 Thanks for reading.

 ](*,)  ](*,)  ](*,)

Hello.  So, I'm trying to get an idea of where your sitting at the moment. Is there an existing XP OS on your box right now and you are unable to boot it, or did you wipe the drive?

You obviously understand the whole bootloader repair process if the answer is the former.  But if indeed you wiped the drive then the drive is infact WIPED.  There is nothing that ubuntu could do to your drive that could not be undone by wiping it.  So ubuntu is not the issue here.  

If you have been able to rule out hardware issues then I would go into the Bios and check your settings.  Maybe the MBR got screwed up and you are unable to fix it because it is write protected.

Check it out!  Good Luck.

---

### Post by Jonie on 2006-08-20
This is hardware problem. And it doesn't really matter what is on your hard disk. Not at all, because XP Setup will access the disk no sooner than it's starting ntoskrnl, i.e. after all necessary drivers are copied into ram. It does take about two minutes and you would see all the messages. XP setup can't even access the disk, because it doesn't have driver for you HDD controller yet.

---

### Post by funchords on 2006-08-20
> **Rez. said:**
> 
 So I go through the usual routine of slipping in my XP disc and booting from it. I get the *'Press any key now to boot CD'* message and do just that. The DVD drives led lights up and for a brief second I get the familliar '*Setup is inspecting your computers hardware'* Message and then - **BOOM!**. Nada. A blank screen and the DVD drive spins down and the led shuts off.

Exactly the same thing happened to me.  It was a bad sector on my hard drive (apparently my computer hung in an endless loop during something disk intensive and the temperature went way north!).  I was able to use SpinRite (commercial, [www.grc.com](www.grc.com)) to recover and relocate the bad sector.  

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) is a disk full of tools, one of these may fix it.  Before getting too cocky, you should try to recover the important  data off the drive.

---

### Post by Rez. on 2006-08-20
> **randell6564 said:**
> Hello.  So, I'm trying to get an idea of where your sitting at the moment. Is there an existing XP OS on your box right now and you are unable to boot it, or did you wipe the drive?

You obviously understand the whole bootloader repair process if the answer is the former.  But if indeed you wiped the drive then the drive is infact WIPED.  There is nothing that ubuntu could do to your drive that could not be undone by wiping it.  So ubuntu is not the issue here.  

If you have been able to rule out hardware issues then I would go into the Bios and check your settings.  Maybe the MBR got screwed up and you are unable to fix it because it is write protected.

Check it out!  Good Luck.

 I do have XP Pro installed on my first partition and Ubuntu on a Third partition. If you look at my original post there is a link to another post I made regarding my trials with trying to get Ubuntu to boot using XP's bootloader. After several tries I gave up and tried to fix the MBR with my XP installation CD. It wouldn't boot. Jonie is correct, It is a hardware problem. Several days ago I swapped out my power supply for a lesser rated one. I have an AMD64 which is pretty demanding on the power side of things.
 Yesterday I disabled my Primary IDE channel in the bios and the XP CD booted fine. Alas, Of course, It didn't find any hard drives. So I'm guessing it was just a comedy of chance. I played around with Ubuntu/XP bootloading unaware that this condition existed. My apologies to Ubuntu. :-# 
 Thanks for the replies and help.

---

### Post by Rez. on 2006-08-20
> **funchords said:**
> Exactly the same thing happened to me.  It was a bad sector on my hard drive (apparently my computer hung in an endless loop during something disk intensive and the temperature went way north!).  I was able to use SpinRite (commercial, [www.grc.com](www.grc.com)) to recover and relocate the bad sector.  

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) is a disk full of tools, one of these may fix it.  Before getting too cocky, you should try to recover the important  data off the drive.

You read my mind funchords, Going to bootup SpinRite in a few ...

---

### Post by Jonie on 2006-08-20
It may be bad motherboard or it may be bad ram, too. Setup is inspecting.... means ntdetect.com is accessing some reserved memory addresses in real mode and somewhere it fails. Good luck!

---

