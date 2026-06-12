---
title: "Computer Takes a Long Time to Boot Because Of Post GRUB Flashing &quot;_&quot;"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by corrytonapple on 2011-01-08
Hello Forum Community!
The other day after a crash after the computer going to sleep, I had to do a force shutdown (This is all another thread).  I went to go boot it up, and I realized how slow it is.  After GRUB, although the HDD is active, I just get a Flashing
```
_
```That stays for exactly 30seconds, making the startup longer than Windows. But including the time it takes Windows to log in to an account makes it that Ubuntu is still the faster OS.
Anyway, how do I remove this? It actually happens twice, but this first time I am talking about is when it is about text size 14px. Then it does it again, but it is about 10px in size.
How can I remove this or make it faster. As stated, this all happens Post GRUB.
Thanks!

---

### Post by corrytonapple on 2011-01-10
Bump

---

### Post by wilee-nilee on 2011-01-10
How about some actual time it takes to get to the login screen, or if you have auto login to the desktop. You say 30 seconds but to what. This is a upgrade from Lucid as well isn't it?

---

### Post by corrytonapple on 2011-01-10
Yes, it is.  Let me restart and will get some accurate times for you.  I will edit this post
Alrighty, 49 seconds for a computer of my specs at not even one year old.  30seconds is a flashing "_" With HDD activity.

---

### Post by wilee-nilee on 2011-01-10
> **corrytonapple said:**
> Yes, it is.  Let me restart and will get some accurate times for you.  I will edit this post
Alrighty, 49 seconds for a computer of my specs at not even one year old.  30seconds is a flashing "_" With HDD activity.

Not sure here but when I look through your old threads you seem to be trying to customize your setup. This if the stuff is starting at startup is going to slow things down possibly. Have you gone to the startup Applications in the menu and turned off what you don't need.

Are you sure your goals are based on any facts, but not conjecture.

---

### Post by corrytonapple on 2011-01-10
I will go through it again.  Seems to be though that GRUB might not be loading or transitioning over to Ubuntu or something. I do not know for sure, but I know for the times as I have counted. Correct, I have.  I just removed some extra kernals that were shown on GRUB and added a background image.  I have no proof that this is not typical  for most installs though.  You may be right about that.

---

### Post by wilee-nilee on 2011-01-10
> **corrytonapple said:**
> I will go through it again.  Seems to be though that GRUB might not be loading or transitioning over to Ubuntu or something. I do not know for sure, but I know for the times as I have counted. Correct, I have.  I just removed some extra kernals that were shown on GRUB and added a background image.  I have no proof that this is not typical  for most installs though.  You may be right about that.

I know my Maverick set up seems to be slower then it had been, but I just don't worry about as it always boots up. I have it set to auto login though so, the time generally looked at is to the login screen. Hopefully others will have an idea though.

---

### Post by corrytonapple on 2011-01-11
I forgot to say I use Auto Login, since the other user does not get on this computer often.  I have to say, Maverick does seem slower that Lynx is/was.  I tried Fedora 14 in VMware and it seems just as slow or slower, but that may be because the VMware is in Windows. May I add this is a brand new install, going on a month old in a week.  When I start Windows or Ubuntu, the HDD activity light is solid green, meaning full activity.  So if there is no problem, maybe Windows just covers it all up better than Ubuntu?  I just do not want to mess anything up right now.  I want to fix my issues than mess it up. :D (That means install Fedora Maybe? Still looking around)

---

### Post by corrytonapple on 2011-01-18
Still, this must be too slow for a Ubuntu install.  May this be a bump.  If all other issues are fixed, then I will stay on Ubuntu.  I would like them fixed by 11.04.  If not, than I will move on to openSUSE 11.3 KDE.

---

### Post by Quackers on 2011-01-18
49 seconds is about what it takes to boot my system too. On one of the installations I get a flashing cursor for about 30 seconds too, but the total time to the desktop (with auto login) is still around 50 seconds. That's fine for me.
If you had a look at what is being done during that time I think you would be amazed that your boot time is so fast! 
I'm quite happy with that time, and I've used XP and Vista :-)

---

### Post by corrytonapple on 2011-01-18
OK.  Well, for as long as that is normal.  Problem, solved.

---

### Post by gbell12 on 2012-03-11
Mine does this too. It's not normal - Fedora didn't do it. It adds a good 10-15 seconds to my boot time which is murder if someone's waiting for me to dual into Windows.

Again, to clarify, this is before the Grub menu comes up. It's post-BIOS/POST but pre-GRUB menu.

No indication from Grub what it's waiting for...

Anybody have any ideas on how to debug this?

---

