---
title: "X Server crashing after upgrade??"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by stumpalump on 2008-05-01
So it was pretty tricky but I finally got the upgrade to finish downloading and installing (from 7.10)

There were only a few things I didn't replace with new versions like my apache2.conf, grub menu.lst (which I edited to point ot the new kernel etc).

But what it did is it tried to load up, showed a terminal login prompt, then started X. Then what happened is it showed my login screen for a second, and then it's like X is crashing over and over again. 

It will show the login for a second, then "crash" and go to the background color with the loading wheel, then reload the login screen again and so on. It's looping perpetually and I can't get it to load! I can't type anything to try and login or anything and I can't click on anything because the mouse just keeps resetting to the middle of the screen before I can do anything.


Anyone have any suggestions? I'd really hate to have to reinstall as well because I tried to upgrade...

---

### Post by chek2fire on 2008-05-01
Try to boot in recovery mode and from there fix xserver.

---

### Post by stumpalump on 2008-05-01
I tried that. I tried copying my backed up xorg.conf file. I'm wondering if it's not a problem with the Xserver at this point and possibly a problem with a program that is loading on startup.


Anyone else have any other ideas?? Please help!

---

### Post by stumpalump on 2008-05-01
Is there something in recovery mode that will check the update and fix any problems??

---

### Post by stumpalump on 2008-05-01
bump. someone please help. I'm thinking this may be related to the session manager. How can I reinstall it?

---

### Post by stumpalump on 2008-05-02
So I have an update. I have been playing with this computer trying to get it back up and running for a few days. I have reinstalled a bunch of things and fixed a bunch of things that were going on but this is the point I'm at now.

Still having the EXACT same issue but I have less errors in my .xsession-errors now. Here's what the bottom looks like

```

Xsession: X session started for stumpalump at Fri May 2 12:10:49 MDT 2008
xrdb: No such file or directory
xrdb: Can't open display ':0'
Setting IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
/usr/bin/xmodmap: unable to open display ':0'
cannot open display:
Run '/usr/bin/seahorse-agent --help' to see a full list of available commands

```

So why the heck can't it start the display?? I don't get it. Someone pleasse shed some light if you know anything

---

### Post by stumpalump on 2008-05-05
bump. I'm still stuck on this. Still researching. If I find a solution I will post it for anyone else having issues.

---

### Post by bobnutfield on 2008-05-05
What video card are you using?  This type of thing has been occuring to some (not all) people with ATI grahics.  Can you long in failsafe (text login.)?  If you can, I would try to change the graphics to "vesa" so that you can get to a desktop.  I don't know if that would help, but others have been able to get a desktop and work at fixing it from there,

Bob

---

### Post by PmDematagoda on 2008-05-05
Did you try reconfiguring the X-Server to it's default/recommended settings using:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
or
```
sudo xfix
```
and then starting the X-Server?

---

### Post by stumpalump on 2008-05-05
> **bobnutfield said:**
> What video card are you using?  This type of thing has been occuring to some (not all) people with ATI grahics.  Can you long in failsafe (text login.)?  If you can, I would try to change the graphics to "vesa" so that you can get to a desktop.  I don't know if that would help, but others have been able to get a desktop and work at fixing it from there,

Bob


NVIDIA 8600 GT. How do I use VESA? Something tells me VESA won't be able to access display 0 either. I think this is a permissions issue that popped up when I upgraded. Can anyone make any suggestions of different permissions to check that I may have missed?

---

### Post by stumpalump on 2008-05-05
> **PmDematagoda said:**
> Did you try reconfiguring the X-Server to it's default/recommended settings using:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
or
```
sudo xfix
```
and then starting the X-Server?

Oh yes more times than you know lol

I am going to try installing the next oldest version of the NVIDIA drivers using envyng and see where I'm at...

---

