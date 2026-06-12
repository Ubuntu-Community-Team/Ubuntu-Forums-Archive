---
title: "Feisty won't do graphics now"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by oVerload7777 on 2007-04-20
I was waiting for what felt like christmas, and finally 7.04 was out and I grabbed a copy, and I left the torrent running. I burn the cd, put it into my dell inspiron 9400 with ATI x1400 and boot it live. I've been living on 6.06 and I'm ready for the upgrade. I tried 7.04 beta and it was amazing!!! but it wouldn't do WEP, and the suspend was acting up. So I've been waiting for the final release hoping that at least my wep would now work.

But all I get is a msg telliong me that X can't start!! WTF!!! Every other version, even the beta's worked on a live boot. But now I have to figure out how the heck to fix the video!! I have no idea how to do it. The only reason I'm using ubuntu is because it just worked. but now I can't.

---

### Post by lightglitch on 2007-04-20
I have the same problem with the livecd and I also tried the beta version and worked without any issue.
I have a laptop with a x1600.

---

### Post by gstool on 2007-04-20
I had the same thing happen.  I had been using the proprietary nvidia driver in 6.10.  Getting to a console prompt and using vi to edit /etc/X11/xorg.conf and change the "nvidia" driver line to "nv" allowed me to startx and get back into graphics, although it was in KDE instead of my normal gnome environment.

From there it was all downhill.  After reboot, I can no longer get into my Ubuntu install.  But hey, upgrading didn't work from 6.04 to 6.10 either!  I hope you have better luck.

Gerry

---

### Post by kennygunie on 2007-04-20
A solution from [french ubuntu document page]("http://doc.ubuntu-fr.org/installation/probleme_ati"):

1.boot with the Ubuntu 7.04 live CD, than F6
2. replace "splash" by "single"
3. <enter>
4. at the terminal enter: 
```
apt-get install xorg-driver-fglrx
aticonfig --initial
aticonfig --overlay-type=Xv
```
5. type "/etc/init.d/gdm start" or "sudo /etc/init.d/gdm start" then <enter>
6. you are on the live CD now

Have fun ;) . Hope ubutu release a new LiveCD for ati, repeat this driver installation every time using the liveCD it's not funny at all :(

---

### Post by oVerload7777 on 2007-04-21
I tried what you suggested, but starting GDM failed.  When i boot from the live CD it plops me to the command line. F6 does nothing but beeps. I saw no reference to splash or single. I did get the ati driver installed, but the overlay command reported "Warning video overlay doesn't affect running sessions.

Am I missing something?

---

### Post by oVerload7777 on 2007-04-22
Is there a way to install from the command line after it boots from the live cd and drops me to the command line? If I could get it installed then at least I could just work on trying to fix my display driver. 

I tried to do a text install from the alt cd, but I just got a black screen :(  

I just wanna get feisty installed and working!!!

---

### Post by ayeizajedi on 2007-04-23
This has been posted before.  I have an inspiron 9400 with the x1400, same issue, when running the boot CD GDM fails to the command line.  The following allowed me to get to desktop and get it installed.

From the command line:

sudo dpkg-reconfigure xserver-xorg

pick all defaults and make sure VESA is selected

remove all video resolutions except 640x480

HorizSync = 36-52
VertiRefresh = 36-60

Save settings

type 'startx'

You should then be able to install it now.

Hope this helps.

---

### Post by oVerload7777 on 2007-04-25
Finally!!!! That worked perfect!!!! Thank you so much!!!

I have ubuntu 7.04 installing right now :)


Thanks again!!!

---

