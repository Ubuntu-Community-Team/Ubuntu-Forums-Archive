---
title: "[SOLVED] Compiz not working, when using live CD it works"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by kortas on 2008-09-25
Hi everybody,

I would like to get compiz effects working on my laptop (intel X3100). When I use Ubuntu live CD, there is no problem with these effects

All I did was that **I moved my Ubuntu system from my old laptop (turion 64, geforce 7150) to my new one (core 2 duo, X3100) using partimager**. First it seemed its not gonna recognize graphics card but finally it loaded however compiz is not working and when I try to enable desktop effects I am getting an error. As I said, **there is no problem with compiz while using live cd**.

I tried to replace /etc/X11 folder with the folder /etc/X11 while live CD is runnig and also ~/.config/compiz but with no success.

Is there any other file where is an information about graphics settings? I think it has to work if live cd does... Or if is there any way of reinstalling windows system..

And also I noticed, when Ubuntu is loading at startup, there is no progress bar. There is just a text output whats going on instead, then graphic login screen normaly appear.

Thank you for any response
Kortas

---

### Post by WWSmith36 on 2008-09-25
You should really install the operating system on the new machine.  Partimage is only good for restore to the same machine.  When an operating system is installed in configures itself based on the hardware that it find that particular machine.  I am surprised that it ran at all.

You might end up finding a whole host of other errors down the road as well.

---

### Post by kortas on 2008-09-25
Thaks for very quick reply. Maybe I will do it, but I didnt wanna lose all my installed programs, screenlets, all the settings etc... So I did it that way.

I could save all the packages now installed by 
dpkg --get-selections > selections.txt
and after reinstall
dpkg --set-selections < selections.txt

That would be great. What about all the settings? I know lots of things are stored in my home dir, but all of them? For example I used Apache webserver and its configuration file is in /etc/apache2/.. so I guess I should backup this file also, if i wanna keep the settings. But I have no idea where is conf file of pidgin, ekiga and all other programs which I wanna backup as well...

---

### Post by WWSmith36 on 2008-09-25
You can backup you all your programs and settings.  Most everything is store in your home folder.  There are a few other directories that you should also backup.  I´m going to see if I can´t get you a good howto for doing it.

---

### Post by kortas on 2008-09-25
I found some threads about it:
[http://ubuntuforums.org/showthread.php?t=687796](http://ubuntuforums.org/showthread.php?t=687796)
or
[http://ubuntuforums.org/showthread.php?t=67407](http://ubuntuforums.org/showthread.php?t=67407)
I have a separate home partition and if I save /etc/* I can restore later only part I need. Thank you WWSmith36

---

### Post by WWSmith36 on 2008-09-25
It just took me a while to find it.  This tutorial will allow to you backup all the packages and programs that you have installed and then reinstall them quickly.  That will you will retain all your settings and programs :)  Just make sure you partition a separate home folder.

[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)

---

### Post by kortas on 2008-09-27
> **WWSmith36 said:**
> It just took me a while to find it.  This tutorial will allow to you backup all the packages and programs that you have installed and then reinstall them quickly.  That will you will retain all your settings and programs :)  Just make sure you partition a separate home folder.

[http://mybrainrunslinux.com/node/2](http://mybrainrunslinux.com/node/2)

I did so. I installed all the packages and after reboot I cant enable desktop effect any more. sh*t

Enclosed I am sending the list of installed packages.

---

### Post by kortas on 2008-09-28
I found a solution. I tried to remove 2 packages with nvidia in their name (I dont have nvidia card apparently) and after reboot it worked! I could do that before, but I am glad I made clean install because of other things.

---

### Post by disneyfriedhistory on 2008-11-26
I'm going to try this out when I get home tonight.  I've been having problems with my graphics card (Thinkpad T30 with Radeon 7500) and Ubuntu on every upgrade after Gutsy.  Each upgrade seemed to make things slower.  When I upgraded to Ibex, compiz wouldn't even start!  

Last night I finally tried out the Live CD for Ibex and it seemed to have everything working correctly. I was excited.  So I did a fresh install of Ibex (while saving my /home partition) last night.  No luck.  

So either the problem is with something in /home, or the install of Ibex makes different driver decisions than the Live CD, or else the problem is something like this.  Here's hoping!

(I also tried out the Fedora 10 Live CD, and it couldn't get compiz to work either.  But Gnome seemed a lot snappier - even with the metacity composite manager enabled!)

Update: tried the above suggestions.  So either the Live CD is setting something up differently compared to when I do a fresh install, or else something in my /home directory is messing things up.

---

### Post by disneyfriedhistory on 2008-12-15
Update on working with Ibex.  I did a fresh install with a new hard drive and compiz began working.  But it was working slowly, and the only way I was able to get it to work with Feisty was to reduce the defaultdepth to 16 in xorg.conf.  Turns out this caused the original problem to reoccur.  Apparently compiz can no longer be run at 16 defaultdepth.  Which means compiz is basically useless.  I'm gonna check on teh compiz boards and possibly try to compile it myself.  Otherwise I'll be permanently downgrading all the way to Feisty for my T30.  Sad news.

---

### Post by kortas on 2008-12-16
I updated to Ibex. Although video window preview (on my X3100) began to work, the computer became also very very slow. Compiz causes problems in other applications such as google earch (the map is black), matlab simulink or open arena. I disabled compiz and all the issues are gone. Compiz is not worth of all the problems.

---

