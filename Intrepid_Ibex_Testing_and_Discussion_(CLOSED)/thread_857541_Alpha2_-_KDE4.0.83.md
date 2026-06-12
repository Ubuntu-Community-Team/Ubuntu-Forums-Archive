---
title: "Alpha2 - KDE4.0.83??"
date: 2008-07-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xebian on 2008-07-12
KDE 4.0.83 is what shipped with Alpha2.  I thought Kubuntu is supposed to be on the bleeding edge, but RC1 to be released next Tuesday is at 4.0.98, and even Debian is at 4.0.85.  :confused:

---

### Post by Nullack on 2008-07-12
Honestly, I keep seeing all these issues with Kubuntu Intrepid. Ive had numerous problems with Kubuntu release versions in the past too thats always led me back to gnome. IMHO Kubuntu doesnt have the resources it needs and your better off using OpenSuse for a good KDE experience.

Ubuntu is strong with gnome but painful on KDE.

---

### Post by caryb on 2008-07-12
We get updates in spits & spurts, last time was 5 weeks between updates. I guess we have 3 weeks to go:)



Cary

---

### Post by caryb on 2008-07-13
Just saw the first KDE4 upgrade in a few days mind you it's 4.0.83:confused:

[https://launchpad.net/ubuntu/+source/kdegraphics/4:4.0.83-0ubuntu1/+build/648472]("https://launchpad.net/ubuntu/+source/kdegraphics/4:4.0.83-0ubuntu1/+build/648472")

---

### Post by caryb on 2008-07-14
Guess what just showed up in the builds [https://launchpad.net/ubuntu/+source/kde4libs/4:4.0.98-0ubuntu1/+build/668700]("https://launchpad.net/ubuntu/+source/kde4libs/4:4.0.98-0ubuntu1/+build/668700"):lolflag:

---

### Post by xebian on 2008-07-14
> **caryb said:**
> Guess what just showed up in the builds [https://launchpad.net/ubuntu/+source/kde4libs/4:4.0.98-0ubuntu1/+build/668700]("https://launchpad.net/ubuntu/+source/kde4libs/4:4.0.98-0ubuntu1/+build/668700"):lolflag:

Good to hear.  These must be the RC1 which will be released tomorrow.:guitar::guitar:

I was amazed the build was done only now.  A huge jump from 4.0.83 to 4.0.98.  It reminded me when 4.1 beta 1 came out, Kubuntu was caught sleeping.  They forgot to build it ( from nixternal blog).

---

### Post by xebian on 2008-07-14
Guess what?  Updated my Ibex just now, and it came up as KDE4.1 RC1 (4.0.98)

:guitar:

---

### Post by jbernardo on 2008-07-14
What mirrors are you using? With archive.ubuntu.com I am still waiting...

---

### Post by xebian on 2008-07-14
> **jbernardo said:**
> What mirrors are you using? With archive.ubuntu.com I am still waiting...

US archive.  
RC1 is much faster.  So fast that you can feel/see it.  Still missing some multimedia though - still at 4.0.83

---

### Post by jbernardo on 2008-07-14
I' d be happy if it fixed bug [#247393]("https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/247393").
I' ve now tried the us mirror and it only updated kdelibs5 and kdepimlibs.

---

### Post by andrek on 2008-07-14
> **xebian said:**
> US archive.  
RC1 is much faster.  So fast that you can feel/see it.  Still missing some multimedia though - still at 4.0.83
I'm running Ubuntu intrepid ibex alpha 2 now - how to install the most up-to-date kde4 ?

---

### Post by ccw on 2008-07-14
> **xebian said:**
> KDE 4.0.83 is what shipped with Alpha2.  I thought Kubuntu is supposed to be on the bleeding edge, but RC1 to be released next Tuesday is at 4.0.98, and even Debian is at 4.0.85.  :confused:

I don't know what exactly 4.0.85 is but if you compare these:
[http://techbase.kde.org/Schedules/KDE4/4.1_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.1_Release_Schedule)
[https://launchpad.net/ubuntu/+source/kdebase/+publishinghistory](https://launchpad.net/ubuntu/+source/kdebase/+publishinghistory)

4.1 Beta 1 (4.0.80) is announced on May 27, ubuntu kdebase is released May 30. (+3 days)

4.1 Beta 2 (4.0.83) is announced on June 24, ubuntu kdebase is released June 23 (-1 day)

4.1 RC 1 (4.0.98) is scheduled to be announced July 15 (tomorrow), ubuntu kde libraries are being pushed out as we speak. (-1 day)

I see no problem here.

[http://packages.qa.debian.org/k/kdebase.html](http://packages.qa.debian.org/k/kdebase.html)
Debian sid/unstable is still running 3.5.9
They got 4.0.84 in experimental

---

### Post by jbernardo on 2008-07-15
Until now only libraries, kdm and kdebase-runtime. Which, unfortunately for me, broke plasma on my machine, and it always segfaults now.

---

### Post by xebian on 2008-07-15
> **jbernardo said:**
> Until now only libraries, kdm and kdebase-runtime. Which, unfortunately for me, broke plasma on my machine, and it always segfaults now.

I'll stick with Debian for now because it's more up-to-date and stable than Kubuntu considering it's experimental.  

I'll probably try it again when it's version 9.10  KK (King Kubuntu?)

---

### Post by plun on 2008-07-15
SOS  :)

Managed to start KDE4   

The terminal is a good thing to know about .....

fusion-icon also worked for Compiz start...:KS


But where is system-settings....  :confused:


I have wrong keyboard.

---

### Post by caryb on 2008-07-15
My Kubuntu is totally screwed today, kdmrc locks up had the cant start kstrartupcong4 error, no write permissions to .kde4 directory no write permmissions to .ICEauthority.

Once all of these were fixed (linking .kde -> .kde4 & changing permisssions) I now have a session. 1 1/2 hours of mods but all is good I learned some things along the way:guitar:


Cary

---

### Post by caryb on 2008-07-15
Adept still requires "root" password then crashes, & the system settings still lacks i.e. no printer admin, networks etc.


Cary

---

### Post by jbernardo on 2008-07-16
Also, I still don't have a "administrator mode" button in system settings (for things like samba or login manager configuration).

---

