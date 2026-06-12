---
title: "Error 15, locked out"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by serendipity576 on 2006-05-17
Hi all,
   I'm a newbie for sure so here's the problem.  I have a new laptop, windows xp preinstalled.  So I use partition magic to give Windows a 20G partition and then reboot from the Ubuntu install cd(downloaded and burned on cd yesterday).  Everything goes fine until I reach the user name/set up password screen.  I type in my information, yet the page comes back again asking me to type in my username and then password again(to set it upagain).  So I do, yet this screen just keeps repeating itself when I try to progress through the installation.  ](*,) ??????  
     Then I just pull the menu up and skip to the rest of the install process, but when I finish and reboot(expecting GRUB), I just get a black screen with "Error 15".  No idea how to fix this and I'm locked out of both windows and ubuntu(assuming it even installed!):rolleyes: .  Anyway, some help would be awesome if you guys could spare it.  Thanks a bunch.

C.

---

### Post by Kapre on 2006-05-17
serendipity - if you have a win boot disk(ette), try to pop it in and boot on it. On the prompt key in "fdisk /mbr" to fix your boot (so you can boot into windows). Question also when you partition your HD, did you back-up and defrag 1st? Reason I'm asking is if you did not do this 1st, you might have damaged/corrupted your windows.

K

---

### Post by serendipity576 on 2006-05-17
Hi, thanks for the advice.  I actually don't have a win diskette, or even a floppy drive actually on this laptop:-k .  Any other ideas?  Assuming I can somehow get back into Windows, should I defrag first and then try the install again?  Using partition magic wouldn't have caused this would it?  It's strange because I installed Ubuntu on my desktop a few days ago with the exact same disc with no problem.

---

### Post by Sef on 2006-05-17
From Gentoo:

> 15. Missing Grub Image

Situation

When booting the system, you do not see that spify Gentoo splashscreen.

Solution

First of all check if the splashscreen file you are referring to in your grub.conf really exists. If that is the case, go and check the grub ebuild. Maybe the patch for the splash image is commented out in the version that you are using.

16. 

Here is rescue disk, it is recommended to run on an cd-rw:

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by serendipity576 on 2006-05-17
Thanks a lot.  I'm going to burn that to cd and try that out.  I'll let you all know how it goes.

Clay

---

