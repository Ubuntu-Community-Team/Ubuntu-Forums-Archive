---
title: "how disable power management in terminal?"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by Vim on 2012-06-19
How can I disable Kubuntu's power management from a command line?
I've searched online for hours, without finding an answer to this question.

---

### Post by Vim on 2012-06-20
I should have mentioned in my previous post that I'm using Kubuntu 12.04 LTS.

[SIZE="1"](The forum software thinks I'm using Ubuntu 8.04.  (I tried to update my profile but the forum software said: "Vim, you do not have permission to access this page. This could be due to one of several reasons:  Your user account has less than 50 posts. ...(etc)".))[/SIZE]

---

### Post by FroL_Onn on 2013-03-05
I have the same question!
The only variant I learned is here [http://forum.kde.org/viewtopic.php?f=22&t=37365](http://forum.kde.org/viewtopic.php?f=22&t=37365)

Briefly, you are to change 
[COLOR=#2E3436][FONT=Open Sans]X-KDE-Kded-phase=1
to
[/FONT][/COLOR][COLOR=#2E3436][FONT=Open Sans]X-KDE-Kded-phase=0
in /usr/share/kde4/services/kded/powerdevil.desktop

and then to start
$ kded4

May be there is an easier way?[/FONT][/COLOR]

---

