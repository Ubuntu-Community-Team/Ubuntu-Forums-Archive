---
title: "I Can't Log On Ubuntu 8.04 Desktop"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by 1611kjb on 2008-04-30
The software installs just fine, but I can't log on. During the installation process it asks me for a username and password and I provide them, but when it is done, it starts the log on process, I hear the music, then the screen goes black and it comes back up asking for a username. If I enter bad usernames or passwords, I get a bad username/password error. When I enter the correct information, it just does this restart thing over and over. I have tried reloading it three times. I even tried running my copy off the CD-ROM. I get a message that says user Ubuntu will log on in 10 seconds. Then it tries, and the same behavior, it starts the log on, you hear the music and then it pops up with the log on screen. What do I need to do? I running it on an Athalon system with 2Gb of ram. I am loading it dual-boot with Windows XP, which worked fine with 7.10. It resides on a separate 8gb hard drive it has all to itself.

---

### Post by Caraibes on 2008-04-30
Try to choose "recovery mode" from the Grub menu. Then you might want to try different options, starting by the "FixX" options...

---

### Post by 1611kjb on 2008-05-01
Well, I tried that on the live installation, obviously it won't work for booting off the CD. So I experimented with the sessions that I could start. None of them work except gailsafe Gnome and failsafe terminal. Every other session type just tries to log on and then returns me to the log on screen.

Is there something I could try once I log on in failsafe mode? I'm not a complete newbie, but I'm pretty green at the moment. I haven't worked with Unix in more than 10 years.

---

### Post by 2hot6ft2 on 2008-05-01
I have the same issue and I have already tried fixing the xserver option. I posted this problem on the wiki and it has yet to get a response. Looks like no one has a clue what the problem is or they just don't have a solution.

I am using 7.10 Gutsy on another partition right now and it works great. Looks like 8.04 Hardy wasn't ready for release yet. Should still be in Beta stage.:confused:

---

### Post by Caraibes on 2008-05-02
-What type of video-card do you have ?

-Which drivers do you use ?

-Have you tried logging in console (alt+f2) and :
```
sudo dpkg-reconfigure xserver-xorg 
```

Then choose the vesa drivers...

---

### Post by scotsimba on 2008-05-02
> **1611kjb said:**
> Well, I tried that on the live installation, obviously it won't work for booting off the CD. So I experimented with the sessions that I could start. None of them work except gailsafe Gnome and failsafe terminal. Every other session type just tries to log on and then returns me to the log on screen.

Is there something I could try once I log on in failsafe mode? I'm not a complete newbie, but I'm pretty green at the moment. I haven't worked with Unix in more than 10 years.

I am having a similar problem and my system configuration is as follow:
ati Radeon 9600 display card
64 bit AMD processor, 2GB RAM
ASUS Vintage AH1 box.
I can login in **failsafe GNOME** session.
I had similar problems when I upgraded to Ubuntu gutsy and by reconfigure display drivers it worked. Unfortunately I do not remember the fix, however it was posted here on the support forum. 
If someone can help, it will be much appreciated.

---

### Post by arctic on 2008-05-02
The problem *can be caused* by conflicting configuration files in your /home folder. Rename all hidden gnome and gtk-related files in your /home folder and try to log in again.

---

### Post by Caraibes on 2008-05-02
Login using the vesa drivers (see my previous post). Then enable restricted repos and install proprietary ATI drivers.

---

### Post by scotsimba on 2008-05-02
Thanks. Solved with the help of roolarks solution and the link is [http://ubuntuforums.org/showthread.p...ighlight=fglrx](http://ubuntuforums.org/showthread.p...ighlight=fglrx). Got a working screen now to check why fire fox will not work. Cheer:

---

### Post by 2hot6ft2 on 2008-05-02
> **Caraibes said:**
> -What type of video-card do you have ?

-Which drivers do you use ?

-Have you tried logging in console (alt+f2) and :
```
sudo dpkg-reconfigure xserver-xorg 
```

Then choose the vesa drivers...

AMD Sempron 3400+ 2.0GHz here 896MB RAM
The video chip is the Integrated ATI Radeon Xpress 200 (on board).
Running the drivers that came with ubuntu.
I have tried installing the proprietary driver that are available before but it resulted in a black screen.
I read yesterday that the drivers have to be configured before rebooting but have been hesitant to try it again.
 
I'm glad to see someone has fixed theirs.

The help is much appreciated

I haven't tried what you've suggested, but I'm willing to give it a shot probably tomorrow, the woman is going to be her in a bit and she wants to do some things on the pc so I better not try it right now. Besides I'm still in 7.10 Gutsy right now with things running that I would rather not interrupt.

"-Have you tried logging in console (alt+f2) and :
```
sudo dpkg-reconfigure xserver-xorg 
```

Then choose the vesa drivers...[/QUOTE]"


**UPDATE**
Found in another post that this wouldn't work but did find out that logging in with Failsafe mode and installing the proprietary video driver then rebooting and selecting Gnome would fix it and it worked in 8.04.

It was the pesky Integrated ATI Radeon Xpress 200 video chip driver causing it.

Thanks for the help.

---

### Post by 2hot6ft2 on 2008-05-02
> **scotsimba said:**
> Thanks. Solved with the help of roolarks solution and the link is [http://ubuntuforums.org/showthread.p...ighlight=fglrx](http://ubuntuforums.org/showthread.p...ighlight=fglrx). Got a working screen now to check why fire fox will not work. Cheer:

That link just takes be back to the main forum page:(

---

### Post by 1611kjb on 2008-05-03
I tried that command from the failsafe terminal. It throws me into a multi-step wizard that asks me about keyboards, but there was no place to pick a video driver. What am I supposed to do after I get into that wizard? 

Someone said roolarks helped them, but there's no post from a roolarks. I typed in the URL from that message, but it doesn't give any information about video drivers or fixing the problem

---

### Post by Caraibes on 2008-05-03
You might want to try installing with the "alternate" cd...
If nothing works, go for Debian...

---

