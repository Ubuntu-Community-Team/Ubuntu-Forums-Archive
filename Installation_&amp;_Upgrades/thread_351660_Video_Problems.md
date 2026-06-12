---
title: "Video Problems"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by pawn63295 on 2007-02-02
Hello,
I am a new user in the Linux community and would like to leave Windows in the dust if i could. My only problem is i am a hardcore gamer. so here goes my issue.

on first live boot with the cd it hangs up after the splash screen.
If i boot into safe graphics mode things are peachy tho.
So once in safe graphics mode in install the cd reboot.
First login looks al good graphically. then i go searching for my Linux ATI drivers.
Heres where things go downhill. I installed ATI proprietary drivers. i see the ATI added to my menu's. then i go and install Cedega engine. everythings goes ok except my opengl test and my 3d acceleration test. but i tried to continue anyway. So i install World of Warcraft. everything with the install goes ok. Then i go to launch WOW but graphics are garbled almost smashed together if you will.

Again i am brand spankin new to Ubuntu

Computer specs;
AMD 64 Bit 3400
Asus K8vse Deluxe
Corsair 2x1gig ddr 400
ATI 9550
Western Digital HD
on board sound
on board NIC

Anyone have any insight here. Thanks

---

### Post by gh0st on 2007-02-02
I don't know how relevent this this but which version of Ubuntu did you install? I.E 64-bit or 32-bit. I have an AMD 64 bit processor in my machine and I go the exaqct same problem with the install freezing after the splash logo. I'm not alone either it seems quite a few people have ad this problem.

I gave up and installed the 32-bit version which worked great and seems to do the job fine. From all the stuff I've read on here a lot of people seem to think that the 64-bit version isn't worth the hassle unless you do really intensive stuff like graphics rendering. It might be a problem with the ATI drivers not liking the 64 bit Ubuntu. Then again it could be a simple config error with the X server (the component that controls your display output).

I don't use ATI so I can't really say much about the driver. If you have 64 bit installed it might be worth trying 32 instead though, that's what I wanted too say.

If you're already on 32bit then I don't know what else to suggest sorry. I'm sure someone more knowledgable will be able to help though.

Hope that helps if you are on 64bit. Otherwise I'm probably not much use sorry. 

Good luck :D

---

### Post by gh0st on 2007-02-02
Here's a quick link to the thread about 64-bit install problems. Doesn't seem to be anyone offering a solution though :-(

[http://www.ubuntuforums.org/showthread.php?t=338149](http://www.ubuntuforums.org/showthread.php?t=338149)

You might also wanna check out this thread about getting the ATI drivers working.

[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)

Hope that helps

---

### Post by pawn63295 on 2007-02-06
I am using dapper drake 32Bit OS.
I think this is more of a driver or hardware acceleration issue because when i try to play a movie through xmms or whatever its called (im at work on Winblows so i dont know the prog name) i get video lag. Driver installation was the very first thing i did after i updated ubuntu. 
Do you have to activate acceleration or opengl. i would assume no and hopefully im right?
It could be ATI i havent heard to much problem on the nVidia side of things but like i said im new to linux so what do i know

---

### Post by gh0st on 2007-02-06
Right it's definitely not 64-bit Ubuntu messing it up then. You're probably right it must be a driver issue. Unfortunately I'm not really an expert on ATI cards, I've never even owned one :) 

So I don't know how much use I can be to you. With NVidia you have to update your xorg.conf file to tell the system to use the Nvidia driver after you've installed it. There is a tool for that edits the file for you with Nvidia, there might be something similar for ATI. Did you try looking in the Hardware section of the forum at the ATI setup guides, there should be some good stuff there.

I found this link in another forum about ATI drivers, might be of some use: [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

I know that's not very helpful, sorry. Another thing you might wanna do is post a thread in the Absolute Beginners section of the forum, there are usually some proper Linux Guru's (unlike me) hanging around there, I'm sure someone can help you out.

Another thing you might wanna try is using a tool like Automatix to install all the codecs and stuff you need for your videos. That can solve a lot of problems if you haven't tried it already. There is a good guide here for Automatix: [http://www.howtoforge.com/automatix_ubuntu](http://www.howtoforge.com/automatix_ubuntu)

Good luck, if I can help with anything else let me know.

---

