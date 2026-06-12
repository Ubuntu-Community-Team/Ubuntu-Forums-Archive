---
title: "Bootup Issues with Karmic"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by yoda2nd on 2009-11-14
I have been using Karmic for the last couple of weeks and I have run into an issue where my computer will start beeping rapidly and lockup durring boot up.  It happens right around the point where the screen switches to the splash screen (one with the ubuntu logo and the scrolling boot messages).  This issue appears to be random, restarting the computer generally fixes it.  

I am at a loss as to what the issue might be.  I have checked the logs and nothing obvious jumps out.  Any help or suggestions would be helpful.

---

### Post by 73ckn797 on 2009-11-14
Do they seem to be system beeps like a possible hardware issue? Once up and running are there any problems?

---

### Post by yoda2nd on 2009-11-14
WOW that was fast! :D

Everything runs fine once I manage to get the system booted all the way.  I can go days without any issues (my system runs 24/7), and then usually logging out and back in again will fix the issue. 

The beeping has no pattern to it, it is just a rapid beep, beep, beep, beep, beep constantly.  This happens right when the boot process switches to the splash screen, so my system is making it past post and the boot menu with out any issues.

Thanks for help.

---

### Post by 73ckn797 on 2009-11-14
Is this your first time using Ubuntu? If not, did you upgrade or do a fresh install? Upgrades seem to be causing many problems.

---

### Post by yoda2nd on 2009-11-15
I have been using Ubuntu for about 6 months.  I did do an upgrade and not a fresh install.

---

### Post by yoda2nd on 2009-11-22
Well after the issue continued to get worse and got to the point that I could not even get the computer to work I played around with a few things.
 
 
 I was unable to get recovery mode to work, it would lock up right after the menu shows up.  It would display several mountall errors and lock up saying Starting up NTP.  Seeing the mountall error I popped in my Live CD, I pulled all of my CIFS mounts out of my fstab and was able to boot again.  However, I now have to go though this every time the boot fails.
 
Also I get an error now saying that usplash failed due to an invalid mem type.

---

### Post by Deptgiy06 on 2009-11-22
> **yoda2nd said:**
> I have been using Karmic for the last couple of weeks and I have run into an issue where my computer will start beeping rapidly and lockup durring boot up.  It happens right around the point where the screen switches to the splash screen (one with the ubuntu logo and the scrolling boot messages).  This issue appears to be random, restarting the computer generally fixes it.  

I am at a loss as to what the issue might be.  I have checked the logs and nothing obvious jumps out.  Any help or suggestions would be helpful.
I was registered at your forum. I have printed the test message. Do not delete, please.
Just wanted to say thanks to everyone for the warm/scary welcome,I'm really looking forward to talk about anything and everything horror related.

---

### Post by 73ckn797 on 2009-11-22
> **yoda2nd said:**
> Well after the issue continued to get worse and got to the point that I could not even get the computer to work I played around with a few things.
 
 
 I was unable to get recovery mode to work, it would lock up right after the menu shows up.  It would display several mountall errors and lock up saying Starting up NTP.  Seeing the mountall error I popped in my Live CD, I pulled all of my CIFS mounts out of my fstab and was able to boot again.  However, I now have to go though this every time the boot fails.
 
Also I get an error now saying that usplash failed due to an invalid mem type.

A fresh install may be the easiest fix since there have been no other recommendations.

---

