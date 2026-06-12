---
title: "Crash during upgrade from Dapper to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Kasper42 on 2006-10-26
Hello!

I was trying to upgrade from Dapper to Edgy. Everything was going fine and Edgy downloaded. Installation had started and it was about 1/3 of the way through when my computer crashed:( 

I was forced to pull the power on my computer and reboot it. Now when I boot up, everything seems to load okay (on the booting screen) with the exception of "Hardware Drivers" which it displays as "failed." Where I would normally go to the login screen. I get the "Problem with Xorg" screen. (I have had this screen before when I messed up configuring my resolution.)

My main problem is that I cannot use my USB keyboard (because the Hardware drivers don't load) to restore an old xorg conf file so cannot login or do anything at all! :( 

So basically, can I upgrade (keeping my settings) from the Edgy Live CD (which I am now downloading) rather than doing a clean install? Also, I have about 100gb of files which I cannot back-up as I don't have that many CDs!

---

### Post by Kasper42 on 2006-10-26
Sorry to double post...

I found a way to get my keyboard working and now I can login (not with graphical interface) However, I cannot get very far as when I do login I just get the message "/dev/null/ Permission Denied" loads of times :( 

Is there anyway for me to resume the Edgy install? What are my options? 

Thanks in advance :)

---

### Post by Kasper42 on 2006-10-26
Really, really sorry to triple post but I have to fix this!

Is there any way I can restore or roll-back Dapper then go onto install Edgy? Or should I in some way continue to try to install Edgy whilst keeping all my settings, if so how would I do this without being able to login?

Please help with this. I'm really stuck...](*,)

---

### Post by 2tim3_16 on 2006-11-21
> **Kasper42 said:**
> Sorry to double post...

I found a way to get my keyboard working and now I can login (not with graphical interface) However, I cannot get very far as when I do login I just get the message "/dev/null/ Permission Denied" loads of times :( 

Is there anyway for me to resume the Edgy install? What are my options? 

Thanks in advance :)

I'm having the exact same problem. Running Xubuntu 6.06, followed the directions on [http://www.xubuntu.com/get]("http://www.xubuntu.com/get") to upgrade to Edgy. When I came back to my computer a while later, the screen saver was running, but it didn't seem to remember my password. I finally had to force a power off. After booting, X fails to load, and when I enter my user name and password, I get "-bash: /dev/null/ Permission Denied" filling the screen.

Anybody else having this problem? Anyone have any solutions?

---

### Post by BliND123 on 2006-11-23
> **2tim3_16 said:**
> I'm having the exact same problem. Running Xubuntu 6.06, followed the directions on [http://www.xubuntu.com/get]("http://www.xubuntu.com/get") to upgrade to Edgy. When I came back to my computer a while later, the screen saver was running, but it didn't seem to remember my password. I finally had to force a power off. After booting, X fails to load, and when I enter my user name and password, I get "-bash: /dev/null/ Permission Denied" filling the screen.

Anybody else having this problem? Anyone have any solutions?

I too am having this problem.  Was using Xubuntu 6.06 and went to upgrade also to Edgy.  Again, came back to find screensaver on and it wouldn't take my password...but then I found this post here:

[http://www.ubuntuforums.org/showthread.php?t=285574&highlight=xscreensaver+password](http://www.ubuntuforums.org/showthread.php?t=285574&highlight=xscreensaver+password)

magicfab posted how to get past screensaver....

Then after I get past screensaver all I see are terminals.  So then I decide to reboot since I doesn't see anything doing anything.  After I get it back up and I put my username and password, things start loading, 2 things Fail (hardware drivers and some missing folder). After that is done, something says can't start X server (my graphical interface, and there is nothing to view to diagnose, its blank), then all I get is that "-bash: /dev/null: Permission denied".

Whats wrong with this?

---

