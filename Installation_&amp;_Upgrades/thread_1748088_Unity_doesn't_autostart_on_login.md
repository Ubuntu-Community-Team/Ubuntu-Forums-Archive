---
title: "Unity doesn't autostart on login"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by epicoder on 2011-05-03
I upgraded from 10.10, and there were no apparent problems during install. However, Unity doesn't start when I use the Ubuntu session from GDM. I have guake terminal installed, which starts correctly, so if I open that and run unity as a background process, everything works perfectly. I would like a solution other than adding it to my startup apps, because I still use GNOME every now and then.

---

### Post by dino99 on 2011-05-03
hm never tried guake, so maybe some usefull errors/conflicts with unity could be found into logs (xsession-errors & /var/log eg: system admin logviewer)

is your graphic driver well activated ? (system admin additional drivers)

---

### Post by epicoder on 2011-05-03
My graphics drivers are up to date and working just fine. OpenGL works perfectly in minecraft, as well as unity once I start it. The only problem is that unity doesn't start when I log in, I have to start it myself. I looked through various logs, it appears that unity simply never starts if I don't start it myself.

---

### Post by ezragsit on 2011-05-18
ok, I made an **update** from the previous version of ubuntu through an **edubuntu dvd** install.
It preserved **all **my settings...
Hellas, even if unity does start from a terminal, it does not on a normal start, as it did not in the previous version. I just know about unity as on an other computer I did a full install, not an update, and there it does start by default.

So, I enhance this topic, **how to determine unity to autostart on login, when it does not do this, but it does start well from a terminal session**? 

It's probable as easy as putting a program in Win's Start Menu or running something as a service ... only ... I just explained from which OS I migrate, so I'm still on the phase of "Wow, Ctrl+Alt+T?, Win+Space? and so..."

It's not the most burning question, but it look's nice and I try to convince my fellow teaching staff that Linux IS a mature option for a computer classroom, even for thus who only now painfully learned all that (Win based) ECDL stuff.

Thanks for any kind answer...

---

### Post by CleverCoder on 2011-05-18
I'm seeing a similar thing. I just installed 11.04 on an older HP zd7260us P4 laptop w/ NVIDIA chipset. I updated to the latest NVIDIA drivers, although the hardware driver tool says it's activated but not enabled. I am manually run "unity" or use "compiz --replace" to get the effects working.

Doing this seems to combine the existing window manager, plus I'm not seeing the icons on the left launcher (maybe a driver bug?)

I'm a little confused about what component gets things rolling and where to look to determine what starts Unity. (Also, what's the 'unity plugin' under the compiz manager? I installed that to help chase down my issues...)

Overall, everything seems to work. OpenGL apps appear to work fine. I'm just not getting all the effects or launcher when I login.

Thanks,
-Sean

---

### Post by syed.rakib.al.hasan on 2011-10-19
totally ugly....... compiz has VERY BAD integration with Unity. I tried to something with compiz and the whole unity was gone forever.
   ](*,)](*,)

However, i have a workaround for it - it works, but it should not called a FIX - it's rather a hack.

From Unity launcher, launch up [COLOR=DarkRed]**Startup Applications**[/COLOR]
There, click the [COLOR=DarkRed]**ADD**[/COLOR] button
In Name: type anything you want
In Command: type [COLOR=DarkRed]**unity**[/COLOR]
Then add this in. \\:D/


Next time you start ubuntu, unity should start at login automatically. However, this should not be called a FIX. This is a bug and we have to solve it this way. 

Really annoyed with the way unity has been so unstable with so many things. 
 :twisted: ](*,)](*,):twisted:

---

### Post by AntonyNk on 2011-11-05
Hi, 

I had the same problem. There was a "metacity --replace" in startup applications.

---

