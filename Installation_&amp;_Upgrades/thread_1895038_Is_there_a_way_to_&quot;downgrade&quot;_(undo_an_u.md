---
title: "Is there a way to &quot;downgrade&quot; (undo an upgrade)?"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by swordsintoplowshares on 2011-12-13
I upgraded from 10.10 to 11.04 Natty, not knowing what I was doing   (newbie here), and Gnome [Or is it  called Ubuntu Classic] is now barely  usable, which I suspect may be a  problem with my graphics card or the  driver. This is the card I have:  00:02.0 VGA compatible controller:  Intel Corporation 82865G Integrated  Graphics Controller (rev 02)

I'm wondering: can I just enter some commands and revert to Ubuntu   10.10? 10.10 was running just fine, I wish I hadn't upgraded. :confused:

Also, someone in another thread said: "While 'Ubuntu classic' proved  unusable, "ubuntu classic (no effects)" worked for me just fine." Is it  possible to enter a command to boot into "Ubuntu classic (no effects)"?  

Much thanks in advance.

---

### Post by fantab on 2011-12-13
Since 11.04 Ubuntu uses UNITY DESKTOP. If you have successfully upgraded to 11.04 you are using UNITY, unless you are on an old computer with low specs, in which case you are in fallback mode.

Internal upgrade to a newer version is messy more often than not. I always CLEAN INSTALL the newer version of Ubuntu, it is safe and clean.

First of all BACK UP your important Data. Then you will either reinstall 10.10 (which will reach its end of support soon) or you can download the latest 11.10 and install it. The later is a better option. 

Hope this helps

---

### Post by swordsintoplowshares on 2011-12-13
Thanks, before I read your reply I had edited my post to be more accurate. 

I need to do a file back-up, but being a newbie, I'll have to post a new  thread about that because I don't know how to do it via the command  line, and the GUI is unusable.

Newbie question: Is it possible to "downgrade" (undo an upgrade), or revert to the version of Ubuntu that was previously on a PC? 
Thanks in advance.

---

### Post by mörgæs on 2011-12-13
With this computer I would recommend Xubuntu.

You need to do a fresh install. It is not possible to roll back to an older release.

You don't have to do the back up from the command line, you can do it from a live boot.

---

### Post by lykwydchykyn on 2011-12-13
To back up your files with a GUI, do this:

 - apt-get install lxde
 - log out
 - change your session to "lxde" at the login screen
 - log in

You'll now have a working, simple desktop environment to do your file backup in before reinstalling.

---

### Post by swordsintoplowshares on 2011-12-14
> **lykwydchykyn said:**
> To back up your files with a GUI, do this:

 - apt-get install lxde
 - log out
 - change your session to "lxde" at the login screen
 - log in

You'll now have a working, simple desktop environment to do your file backup in before reinstalling.


Thanks for the LXDE instructions, just 1 newb question: how do you change the session to lxde?

---

### Post by fantab on 2011-12-14
> **swordsintoplowshares said:**
> Thanks for the LXDE instructions, just 1 newb question: how do you change the session to lxde?

You can choose your LXDE Session from your Logon Screen.

---

### Post by mastablasta on 2011-12-14
> **fantab said:**
>  
Internal upgrade to a newer version is messy more often than not. I always CLEAN INSTALL the newer version of Ubuntu, it is safe and clean.

 
maybe, but it's shoved to the users faces with often annoying popup, so IT SHOULD WORK!
 
> **mörgæs said:**
> With this computer I would recommend Xubuntu.
 
That is true, Xubuntu is a very good alternative. and even give that good old Gnome look&feel.
 
However if you still want to use Ubuntu Unity interface there is a way. you see Unity uses hardware acceleration. However some cards (like older Intel) don't have good support for that in Linux. That's why the whole hting works slow or poor on your maschine. 
 
But there is Unity 2D available for those users with older GPU chips. It should work well with your card and basically looks almost the same as original unity providing you still have enough ram and strong enough CPU (which you most likely do since you ran 10.10 before).
 
 
> 
You need to do a fresh install. It is not possible to roll back to an older release.
 
You don't have to do the back up from the command line, you can do it from a live boot.
 
To do a GUI backup there are a couple of distributions availabel that will do it with a nice GUI and liveCD:
 
One is Clonezilla (powerfull, but a bit unfriendly GUI) the other two that are easy for newbies are in my signature.

---

### Post by swordsintoplowshares on 2011-12-14
Thanks to everyone for all the advice--I finally have a usable machine  again! I think the webmaster should add a donate button to the support forums. :smile:

---

