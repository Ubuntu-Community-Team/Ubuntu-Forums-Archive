---
title: "Natty crashes to black screen but is still running"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by u-noob-tu on 2011-04-29
At random times, natty crashes for no obvious reason. The desktop will freeze for about 3 seconds, and then everything goes black. But it seems that everything is still running, because I was able to hit ctrl-Alt-f1 and it worked. This has happened ever since I upgraded to natty yesterday, but is becoming more frequent. 

Thanks in advance

---

### Post by dino99 on 2011-04-29
what are you calling "crash" ?

is there something into /var/crash ?

might be a driver issue, is it activated ? (system admin additional drivers)
or is it a suspend/hibernation issue ? what are the settings ?
or a borked screensaver ?

have you some ppa not updated ?

---

### Post by u-noob-tu on 2011-04-29
> **dino99 said:**
> what are you calling "crash" ?

is there something into /var/crash ?

might be a driver issue, is it activated ? (system admin additional drivers)
or is it a suspend/hibernation issue ? what are the settings ?
or a borked screensaver ?

have you some ppa not updated ?


What happens is everything onscreen stops, mouse, video, everything, and hangs for about three seconds. Then the screen goes black, but with no error message of any kind. Just a black screen. All I can do is restart my computer by holding the button. It's not a screensaver/hibernate issue because this happens while I am using my computer. I'm considering just backing up my home folder and just reinstalling (I had a somewhat troublesome install).

---

### Post by cespinal on 2011-05-01
+1.... same problem here.... screen becomes lines and then it comes back. I can move the mouse cursor but nothing else.

---

### Post by davidself1001 on 2011-05-01
I have a similar issue.  If i walk away for an hour or so when i return i either have a red screen or a screen saver frozen and in either case the system is non-responsive and i have to do a hard reset.

---

### Post by fatcharlie on 2011-05-01
I have the same problem with two of my PCs, black screen with Natty.  I get the black screen if I leave the PCs idle for a few hours.  Just a black screen with the curser.  Nothing works except powering the PCs off and powering up again.  One PC is an upgrade to 11.04 from 10.10, the other an upgrade from 8.04 Ubuntu (which I truly loved for the past 3 years!  What a rock hard stable system).  Both machines are IBM Thinkcentres, dual core.

---

### Post by cespinal on 2011-05-01
Must be a nasty nasty bug.... 

8.04 was a great system... but I remember it also had its very humble, buggy beginnings...

---

### Post by u-noob-tu on 2011-05-01
I think this is more of a problem with unity than natty. It has happened once I reinstalled (complete wipe, fresh slate). I suddenly see a black screen and hear the logout tone. I can type in my password and hear the login tone but still see nothing.

---

### Post by komealy on 2011-05-05
I don't get a black screen, I just get a frozen image and a looping second of what was said by the person I was chatting to. Nothing is responsive at all, the only thing that indicates an error (other than the obvious) is my caps, num, and scroll lock lights are flashing. This only happens about 14 minutes into a video call, voice calls seem to not be affected. It has nothing to do with screensaver or sleep (I disabled them both, same problem). If I runUbuntu classic (normal gnome) it still happens. I will try to post this to skype dev too since I really think that it is a skype issue. Since I installed skype via the Canonical Partner Repo, I figured it belonged here too.

--Kris
AMD AthlonII X2 3.0Ghz
8GB RAM
Natty_x64
Skype2.2.0.25 (Installed from Canonical Partner Repo)

---

### Post by memilanuk on 2011-05-10
anybody find a solution to this?  

About every other time I walk away from my laptop long enough for it to go into screensaver mode (plugged into the wall, with power management set to *not* suspend while on AC power) more than a few minutes, I come back and I can move the mouse, but get no login prompt.  Have to hard-reboot the machine (sorry, don't have another terminal to log into it from), which is kind of starting to such as I lose whatever I had open working on...

---

### Post by memilanuk on 2011-05-10
Alright, I managed to remember from waaay back in the day with Slackware and stuff about Ctrl+Alt+F1 thru F6; got me to a console login.

I did manage to reboot the machine a bit more 'gracefully' than just power-cycling it; still not able to find what the heck is causing this.

'top' showed something interesting:  It noted '1 zombie' process.  I'm going to take a wild guess thats probably the culprit; now how do I find it?

---

### Post by Darth Trix on 2011-05-25
> **memilanuk said:**
> anybody find a solution to this?  

About every other time I walk away from my laptop long enough for it to go into screensaver mode (plugged into the wall, with power management set to *not* suspend while on AC power) more than a few minutes, I come back and I can move the mouse, but get no login prompt.  Have to hard-reboot the machine (sorry, don't have another terminal to log into it from), which is kind of starting to such as I lose whatever I had open working on...

I've the same problem. My video card is an integrated Intel

---

### Post by mrblonde1369 on 2011-05-29
> **komealy said:**
> I don't get a black screen, I just get a frozen image and a looping second of what was said by the person I was chatting to. Nothing is responsive at all, the only thing that indicates an error (other than the obvious) is my caps, num, and scroll lock lights are flashing. This only happens about 14 minutes into a video call, voice calls seem to not be affected. It has nothing to do with screensaver or sleep (I disabled them both, same problem). If I runUbuntu classic (normal gnome) it still happens. I will try to post this to skype dev too since I really think that it is a skype issue. Since I installed skype via the Canonical Partner Repo, I figured it belonged here too.

--Kris
AMD AthlonII X2 3.0Ghz
8GB RAM
Natty_x64
Skype2.2.0.25 (Installed from Canonical Partner Repo)

same problem here with skype!

---

