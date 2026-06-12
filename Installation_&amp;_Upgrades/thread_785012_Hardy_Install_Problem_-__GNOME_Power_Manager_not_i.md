---
title: "Hardy Install Problem -  GNOME Power Manager not installed correctly"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by sa125 on 2008-05-07
I've installed the final release of Hardy Heron (8.04 LTS) a couple of days after it came out, and soon after I started getting system pop-ups that read: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=69072&stc=1&d=1210141131[/IMG]

Any ideas on how to resolve this? 

Also, when I try to reboot my system, it takes over a minute from the time I press the shutdown menu button until the actual menu appears (the one showing the shutdown options - restart, logoff, shutdown, switch user, etc.). I was wondering if that's related and if there's anything I could do to speed things up.

Thanks!

---

### Post by sa125 on 2008-05-09
Nobody?... I can't be the only one who's been having this problem.

---

### Post by melvis02 on 2008-05-12
Hey, I just ran into the same issue last night.  I can't think of anything in particular that would have triggered this happening either.  I reinstalled gnome-power-manager and am not getting that error any more, but everything looks horrid and is running terribly.  Fonts are giant and everything looks like gtk1/windows95 awful grey.

Compiz is still up and running, and most everything seems to work but I'm not too thrilled with the GTK1 look..  I'm starting to wonder if it's something in gConf or a config directory in my home directory got wiped.

---

### Post by melvis02 on 2008-05-12
So I needed my laptop for work tomorrow and didn't feel like doing real troubleshooting, so I took a hammer to it...  I installed xbuntu-desktop just so I would have a fallback DE, then completely removed (purged) gconf and gconf-common.  This whacked just about everything gnome.  I then reinstalled ubuntu-desktop, Ctrl-Alt-Backspaced then restarted GDM and all was well.  Granted you're going to lose a lot of settings probably, but I wasn't so concerned with that.

Please post if you figure out the real cause and how to fix it properly, but this at least gives you the opportunity to clean things up if you're impatient like me.

---

### Post by Oldsoldier2003 on 2008-05-12
> **melvis02 said:**
> So I needed my laptop for work tomorrow and didn't feel like doing real troubleshooting, so I took a hammer to it...  I installed xbuntu-desktop just so I would have a fallback DE, then completely removed (purged) gconf and gconf-common.  This whacked just about everything gnome.  I then reinstalled ubuntu-desktop, Ctrl-Alt-Backspaced then restarted GDM and all was well.  Granted you're going to lose a lot of settings probably, but I wasn't so concerned with that.

Please post if you figure out the real cause and how to fix it properly, but this at least gives you the opportunity to clean things up if you're impatient like me.

reinstalling gnome-power-manager and restarting fixed the problem for me earlier when i was building a minimal install for a chroot...

---

### Post by hackerseraph on 2008-07-09
the reinstallation of the gnome power manager did not fix the problem for me; any other options?

---

### Post by hackerseraph on 2008-07-09
nevermind i fixed it with

sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)


;) seems I just need to re-register everything; to verify my actiosn if you dont trust me check this 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446212](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=446212)

---

### Post by JDVyska on 2008-07-31
Thanks a bunch!  I updated my laptop (that I hadn't updated in an age) last night and it was major mucked up visually.  I was getting the same error message and your solution worked:

```
sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)
```

Other funky things that I experienced pre-fix (so people searching might find this too):

 Gnome menu icons disappeared / vanished
 Gnome Power button turned into a green running man icon
 Help button for Ubuntu in Gnome Panel turned into a life preserver
 Resolutions were all sorts of strange
 The human theme looked wrong and human wouldn't re-apply (it seemed)

Thanks so much!

---

### Post by GixGidea on 2008-08-05
> **JDVyska said:**
> Thanks a bunch!  I updated my laptop (that I hadn't updated in an age) last night and it was major mucked up visually.  I was getting the same error message and your solution worked:

```
sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)
```

Other funky things that I experienced pre-fix (so people searching might find this too):

 Gnome menu icons disappeared / vanished
 Gnome Power button turned into a green running man icon
 Help button for Ubuntu in Gnome Panel turned into a life preserver
 Resolutions were all sorts of strange
 The human theme looked wrong and human wouldn't re-apply (it seemed)

Thanks so much!

Thank you so much for posting both of these bits of information.  
I'm rather new to linux and before I found this thread I was tempted to go back to windows.  
I ran into the same thing after I installed updates yesterday (8/5/08).  I was using my TV and an ATI graphics card and I had the same problems as mentioned above.  
In addition the font seemed ridiculously small.  

I also reinstalled Ubuntu 4 times since I had very little on the computer anyway.  Try this method out before you did what I did. 

Thanks again so much for the help and descriptions.

---

### Post by hackerseraph on 2008-09-06
yeah every now and again i use it when i get a white screen; took me forever to find the fix on the net :D

---

### Post by KPDXHAM on 2009-12-22
Same error with karmic koala, but I believe I caused this one myself! For a few weeks now I've finally been enjoying Ubuntu without having a problem. Had it all tweaked-out the way I want it. Then, I decided I would just try to make a back-up using sbackup. All was going fine, far as I could tell since there's no GUI indicator showing the progress of the backup, well, I thought it was done and rebooted for whatever reason. It was looking like normal bootup until I got the same message 'GNOME Power Manager not installed correctly. Please contact your system administrator.'

Since then, I tried the following from the live Ubuntu 9.10 cd:

sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)


The reason this didn't work for me is that I don't know just how to "fill-in the blanks" so to speak.
It would be really great to be able to fix this present system, or at least retrieve my configuration and "stuff" that I've accumulated. If not, I'll just start over again. Lost count on how many times I've reinstalled Ubuntu in the past few months. I'm trying to get it set-up like we have xp on our 2 computers. If I could do without M$ I would, but at present it's almost like one step forward, two backward.](*,)

Dual Booting with WUBI

Main HDD Win XP

Slave HDD Ubuntu 9.10 (Primary Boot)

If there's someone out there that would help me either get this to boot normal, or retrieve my stuff, this would be greatly appreciated! :)

I've attached a screen picture showing my Ubuntu drive partition.
Let me know if you need more info and how to find it through the terminal.

Thanks,
Cliff

---

### Post by lotfipi on 2010-03-27
I have met this problem in my desktop after some work.
I tried with :

sudo apt-get remove gnome-power-manager

now it was running ok!

hope to avail 
Abdellatif

---

### Post by dpacmittal on 2010-04-12
This might be of help:
[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

---

