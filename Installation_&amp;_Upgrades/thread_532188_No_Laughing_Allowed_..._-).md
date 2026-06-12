---
title: "No Laughing Allowed ... :-)"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by tbohon on 2007-08-22
New to Ubuntu but not to Linux (experience with both RH and SuSE) or programming/systems work (41+ years).

Just installed 7.04 and then did a manual install of the desktop.  My question now is, how in the heck do I get the desktop to start up?  The RH and SuSE autostart in X mode ... so I've never had this problem.

And again, no laughing at the old guy allowed on this, Ok?  :)

Thanks in advance.

Tom

---

### Post by taurus on 2007-08-22
Which desktop (window manager) did you install?  Logging in first with your name and password and run

```
sudo /etc/init.d/gdm start
-or-
startx
```

---

### Post by scrooge_74 on 2007-08-22
which desktop 

for Gnome  gnome-session
KDE  startkde
Xfce  startxfce4

You can also install gdm so it takes care of it.

You have lot more experience than I do so I would not laugh ;)

---

### Post by tbohon on 2007-08-22
Thanks to both of you.  I was reading additional information on installation and realized that I never got the graphical installation ... so put the CD back into the drive and rebooted the machine to see what I'd done wrong.  Saw the 'boot from first hard drive' option, selected it and here i am in a graphical environment!!!

Appreciat e thehelp.  And I really *really* *_really_* like Ubuntu ... I can see why everyone whose comments I've read on distros has raved about it.

Have a great day!!!

Tom

P.S.  Scrooge_74 - I was trying to funny with my 'no laughing' comment.  All this experience means two things - first, I've seen a lot of issues and have resolved them and second, I'm OLD!!! :)

---

### Post by scrooge_74 on 2007-08-22
I understood you from the beginning, I was dieing to laugh. Still you have lots more experience than I do, I been using computers since the days Atari made computers (I am kind of getting old), but never in the programming field.


:lolflag:

---

