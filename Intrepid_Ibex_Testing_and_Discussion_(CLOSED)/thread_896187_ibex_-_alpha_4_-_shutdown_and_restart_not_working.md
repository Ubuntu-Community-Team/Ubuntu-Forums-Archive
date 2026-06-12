---
title: "ibex - alpha 4 - shutdown and restart not working"
date: 2008-08-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by albeej on 2008-08-20
I did a new install from the intrepid dvd of alpha 4.  Shutdown and restart do nothing when clicked in the GUI.  If I give the commands as sudo in the terminal they work.  I can live with that but they certainly should work in the GUI. Has anyone seen this?  Thanks.  John Albee [email]albeej@mchsi.com[/email]

---

### Post by tamoneya on 2008-08-20
> **albeej said:**
> I did a new install from the intrepid dvd of alpha 4.  Shutdown and restart do nothing when clicked in the GUI.  If I give the commands as sudo in the terminal they work.  I can live with that but they certainly should work in the GUI. Has anyone seen this?  Thanks.  John Albee [email]albeej@mchsi.com[/email]

I think this is a known bug.  Look here: [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/250506](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/250506)

It isnt identical but it sounds as if it is related.

---

### Post by Sef on 2008-08-20
Moved to  Intrepid Ibex Testing and Discussion.

---

### Post by Ayuthia on 2008-08-20
Yes, it was discussed over here:
[http://ubuntuforums.org/showthread.php?t=894567](http://ubuntuforums.org/showthread.php?t=894567)

For the Intrepid Ibex related info, you can find most of them over at Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming  > Intrepid Ibex Testing and Discussion

EDIT:
tamoneya and Sef's posts beat me to it.  I hate living with dialup....

---

### Post by albeej on 2008-08-20
> **tamoneya said:**
> I think this is a known bug.  Look here: [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/250506](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/250506)

It isn't identical but it sounds as if it is related.

Thank you very much.  I might switch to xfce or kde and see if the problem disappears there - as one post suggested.  Again, Thanks.  John

---

### Post by gjoellee on 2008-08-23
this is one of the most common bugs in Intrepid at the moment

---

### Post by ronacc on 2008-08-23
> **gjoellee said:**
> this is one of the most common bugs in Intrepid at the moment

and very anoying :confused:

---

### Post by LittleKoy on 2008-08-23
Same here.
But I prefer this way, because in hardy when I tried to shutdown using the GUI it simply crashed, at least now it does no good but no damage either :D

---

### Post by danbuter on 2008-08-23
Shutdown works fine in kubuntu and xubuntu intrepid.

---

### Post by lancest on 2008-08-23
It looks to me like the developers haven't finished Ubuntu-izing gnome since I can still see the gnome style shutdown widget. I often enjoy the CLI shutdown command anyway.

---

