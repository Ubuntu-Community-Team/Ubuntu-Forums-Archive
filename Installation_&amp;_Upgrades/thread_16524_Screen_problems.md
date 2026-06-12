---
title: "Screen problems"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by stijnb on 2005-02-22
Hi ,
I have some screenproblems with my Dell C600 laptop (with a ATI mobility M3 videocard). 
The installation of Ubuntu goes well but in the center of the screen I get flickering part (a rectangle from the upperpoint to lowerpoint of the screen). I didn't install any drivers yet. 
I got the same problems with gentoo (fvwm / i now use gnome) . 

Greetings 
Unzip

---

### Post by largo on 2005-02-22
I think you need to adjust the values in the xfree config file wich resides in /etc/X11...

---

### Post by stijnb on 2005-02-23
What values should i adjust?

U do mean the /etc/X11/XF86Config-4

thx for the reply

---

### Post by Seazzy on 2005-02-24
I had the same problem. 
Comment out (put # in front of) the highest resolution in the /etc/X11/XF86Config-4 file, or just delete them outright. That fixed the problem for me in my user, but  I still get the flickering in the login screen.

Hope that helps.

---

### Post by stijnb on 2005-02-25
Can u Post that file or send it to my email (stijnbrouwers@gmail.com)? Cz I'm a REAL n00b so... I don't really know what i should change. If u give me ur file it will become clear

Thx

---

### Post by bennyp on 2005-02-28
[QUOTE=stijnb]Can u Post that file or send it to my email (stijnbrouwers@gmail.com)? Cz I'm a REAL n00b so... I don't really know what i should change. If u give me ur file it will become clear

Thx[/QUOTE]
 If you use Seazzy's exact file you may break more things than you fix.
What I recommend you to do is open a terminal and do the following commands.

sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.old
sudo nano /etc/X11/XF86Config-4

This will backup your X Server configuration and then epon it in the nano text editor.

When you have begun editing the file, scroll down untill you see a list of desktop resolutions like 
"1280x1024" "1024x768" "800X600" "640x480" 
and then delete all instances of the string "1280x1024"

If that does not solve your problem, I reccommend that you find out the horizontal and vertical refresh (aka sync) rates of you monitor from the manufacturer's documents and then substitute the XF86Config values for horizsync and vertrefresh in the monitor section of the XF86Config-4 file

Don't worry about being new to linux, as long as you think logically and aren't afraid to open a terminal, you'll be fine.

---

