---
title: "[SOLVED] Well, I think I know what the problem is..."
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by abeautifulbeat on 2008-09-24
Hey all!  I'm new to Ubuntu and I'm having trouble installing it.   I'm a complete beginner regarding advanced computer functions.  But I *am* 99% sure that the root of the problem is my AMD ATI Radeon Xpress 200 video card.    

I had already test driven Ubuntu with Wubi, loved it so much I want to install it properly.  In Wubi I was having trouble logging in after I had installed it, but I found this invaluable thread: [http://ubuntuforums.org/showthread.php?t=872376](http://ubuntuforums.org/showthread.php?t=872376)  

I was basically having the same problem as the user who started the thread. They **also** had an AMD video card. The solution that worked for me is near the end.  Login in failsafe mode, go to System > Administration > Hardware Drivers then select the ATI driver.  Completely solved the problem and it was smooth sailing from there!

I've unistalled Wubi and I'm trying to install Ubuntu.  But when I booted up the cd and selected to install it I got this full page of some error message repeating itself over and over, I forget what it is.  

So I tried selecting the "Try without installing" option so I could activate the ATI drive.  But it goes to the login screen and I can't get past it!  I tried using root for the username and password, and ubuntu, and some other things, but I can't get past it!!!  I also tried the failsafe mode each login attempt.

In addition to the aforementioned thread, these users also had the same problem and they all had AMD video card:

 
[http://ubuntuforums.org/showthread.php?p=5467065](http://ubuntuforums.org/showthread.php?p=5467065)

[http://ph.ubuntuforums.com/showthread.php?t=851318](http://ph.ubuntuforums.com/showthread.php?t=851318)

[http://www.techspot.com/vb/topic91072.html](http://www.techspot.com/vb/topic91072.html)

Sorry for the long post!

---

### Post by overdrank on 2008-09-24
HI and welcome, have you checked the cd for errors, and you may want to do a checksum if you have burned the cd.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also have you tried any options under F4 at the start or install screen?

---

### Post by abeautifulbeat on 2008-09-25
Overdrank, thanks for replying!  I'll keep that in mind next time I start a thread. 

I've installed Ubuntu!  Upon boot up, I just tried selecting the Install option again, and to my surprise it did start the installation process.  Of course, when it came time to log in, I did have to use safe mode and then activate the ATI driver. 

I was afraid I wouldn't be able to install because of the other unresolved cases, but I'm very glad I did somehow! :)

---

