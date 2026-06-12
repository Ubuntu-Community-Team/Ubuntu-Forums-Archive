---
title: "i386 or amd64?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by CVDpr on 2005-10-14
Hey there a Windows Mamas-boy here..

Can i install the 5.10-i386 in an Athlon-64, Or its recommended to use the 5.10-amd64, cuz i dont want to have 32apps-bits issues.

So what all of you recommend to me? THX

---

### Post by renderedbrian on 2005-10-14
Would you be happy to compile the odd bit of software which isn't on breezy 64bit by hand?

If not then I'd say go for the i386 build of ubuntu.

64bit is nice to use, however it is a bit leading edge so don't expect everything to work quite as easy as 32bit linuxes (i.e. windows codecs / flash etc).

I'm happy using 64bit ubuntu (I'm preparing to install breezy badger this weekend). But it has been a bit of a rough ride at times getting things to work.

regards

-- 
Brian

---

### Post by tseliot on 2005-10-14
[QUOTE=CVDpr]Hey there a Windows Mamas-boy here..

Can i install the 5.10-i386 in an Athlon-64, Or its recommended to use the 5.10-amd64, cuz i dont want to have 32apps-bits issues.

So what all of you recommend to me? THX[/QUOTE]
You should definitely use Ubuntu 32bit (i386) as it would make things easier. BTW I have tried them both.

---

### Post by Jackster on 2005-10-14
im guessing installing the i686 kernel or k7 afterwards would also work?

---

### Post by Biased turkey on 2005-10-14
[QUOTE=CVDpr]Hey there a Windows Mamas-boy here..

Can i install the 5.10-i386 in an Athlon-64, Or its recommended to use the 5.10-amd64, cuz i dont want to have 32apps-bits issues.

So what all of you recommend to me? THX[/QUOTE]

I'm asking exactly the same question to myself , interesting thread.
I run Ubuntu 5.04 32 bits  on a daily base and Gentoo AMD64 . I have to admit that so far I didn't have any problem at all with Ubuntu 5.04, everything works nicely: video ( Mplayer, Xine ), all the games  etc...
So after reading all the interesting ( and wise ) opinions in that thread I think I'll stick with the 386  5.10 version 

What makes me sad is by the time a new Ubuntu version will be released ( 18 months from now )  my great 64 bits AMD CPU and my Geforce 6600 will be just good enough to end in my Linux firewall-router :)

---

### Post by CVDpr on 2005-10-14
Thx, so with the i386 i can run 32,64bits-apps 
but,
with the amd64 64bits-apps only(32bits-apss-compiling :( )

so Thx for the replys.. so 5.10-i386 here we go..

---

### Post by PhilOSparta on 2005-12-06
I bought a new AMD Athlon 64 with ATI Radeon Xpress 200.  This was packaged as a Compaq SR1630NX.   I loaded it with the i386 iso CD.
A little tweaking of the xorg.conf file and loading the fglrx drivers to replace the ATI stuff had me up and running.

Several ticklish items remain.
1. The panel clock applet is running at 2X.  i.e.  In one real hour, two hours accumulate.
2. The panel "System Monitor" applet shows 50% use, but opening the system monitor application shows 2 to 3 %.
Edit:  Found the fix at this location.
 [http://ubuntuforums.org/showthread.php?t=53094&amp;highlight=double+clock](http://ubuntuforums.org/showthread.php?t=53094&amp;highlight=double+clock)

My original question was, should I load the amd64 iso instead of the i386?  On another thread I found that the 64 bit version has problems which are due to multimedia applications not being written for it yet particularly windows codecs and flash.  Many other programs are written only for 32 bit libs as well and the way around that is installing a chroot enviornment.   

For now I will be sticking with the i386 version, keeping an eye on the 64 bit development in the future.

---

