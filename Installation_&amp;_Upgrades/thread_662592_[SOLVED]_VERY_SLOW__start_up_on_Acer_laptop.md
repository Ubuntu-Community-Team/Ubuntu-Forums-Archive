---
title: "[SOLVED] VERY SLOW  start up on Acer laptop?"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by Russty of Oz on 2008-01-09
I have just installed 7.10 on my Acer laptop and it takes about 5min. from boot to login!  I had an earlier version on this laptop before and it worked well.  Also, while waiting all this time, all I get is a black screen, no indication that anything is happening.  Is there anything I can do to speed it up?  Gutsy works like a dream on my desktop pc.  The laptop has  ATI X700 graphics and I installed the ATI graphics drivers as well.

Russty.

---

### Post by Gina on 2008-01-09
This may be caused by it trying to set too high a resolution for the screen.  Earlier versions used 1024x768, Gutsy uses 1280x1024 as default.  This can result in very slow boot-up and/or blank screen.  This fixed it for me :-

Open Terminal and enter :-
sudo gedit /etc/usplash.conf

The text editor will open and show the following :-
# Usplash configuration file
xres=1280
yres=1024

This wants editing to :-
# Usplash configuration file
xres=1024
yres=768

Change the values, Save and Exit.

However, we're not quite done yet.  Use the following :-
sudo update-usplash-theme usplash-theme-ubuntu

That fixed it for me.  Reboot and you should see the usual orange loading screen.  (If your max screen res is less than 1024x768 then use the appropriate values.)

---

### Post by Russty of Oz on 2008-01-09
[SIZE="4"]**THANK YOU,   THANK YOU,   THANK YOU!!!**[/SIZE]

That has done it!   It is amazing how something so simple can make all the difference.  I just wish I knew all these codes that are required to fix things, I can search the forum for hours at times and still not find the answer I want.   

I am happy now, just have to find out why Fusion has stopped working tonight?  

Russty. :D):P

---

### Post by Gina on 2008-01-09
Great :):)  Yes, it's often the simple things that cause the biggest headaches!.  I have been using Ubuntu for nearly a year now and installed it on several PCs.  I've also persuaded several friends to try it and have set up a beginners [HowTo website]("http://www.ginad.org.uk")  I am collecting problems and solutions to post on there.

---

### Post by Moonwings on 2008-01-15
As Russty so well put it...
THANK YOU THANK YOU THANK YOU!!!!
Problem #1 is now solved!
Now if only problem #2 would get fixed so quickly.  Broadcom wireless chipsets are just not Linux friendly :(
But that is a subject for other posts....

By the way, this was a Gateway laptop which apparently has the same problem with the screen resolution.

---

### Post by EmilW on 2008-01-29
> > **Moonwings said:**
> As Russty so well put it...
THANK YOU THANK YOU THANK YOU!!!!
Problem #1 is now solved!
Now if only problem #2 would get fixed so quickly.  Broadcom wireless chipsets are just not Linux friendly :(
But that is a subject for other posts....

By the way, this was a Gateway laptop which apparently has the same problem with the screen resolution.


Thank you!  Excellent fix!  I had been living with the extraordinarily slow boot (~4 minutes) on my Acer Travelmate 4400 since installing Ubuntu 7.10.   Now with this new graphics assistance, I am booting in less than a minute.  Shew!

Regarding the Broadcom wireless chipset, I found that Google hosts a web page specifically for Ubuntu running on Acer laptops.  Whooda thunk it?

[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

This was the largest piece of the puzzle.  After I followed the instructions on the above site, the rest was relatively easy: Ubuntu made configuring fairly easy.

Good luck.
Emil  :)

---

### Post by Guilden_NL on 2008-01-30
Just installed the latest Fiesty clean instead of upgrading (which had previously done.)  Scratching my head as to why this was now loading three times slower than Vista on the same Acer!  Many thanks Gina, I am able to sleep well tonight knowing I am 95% recovered.

I installed SUSE and the GRUB really hosed up my MBR and Ubuntu file system.  I've never run into this before, so had to take some large measures to recover.  With Ubuntu, it was quicker just to do a clean install.  Of course this popped up and I was pulling my hair out.

Off to some real slumber.=D>

---

### Post by wavesound on 2008-02-24
Hi many thanks!
This worked on my old IBM T40.
Cheers
Bob

---

### Post by Jake-UK on 2008-03-07
Just installed it and did a quick 'google' and found Gina's fix. Great thanks.:)

---

