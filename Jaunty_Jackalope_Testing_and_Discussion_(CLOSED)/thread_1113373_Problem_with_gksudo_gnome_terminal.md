---
title: "Problem with gksudo gnome terminal"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xeddog on 2009-04-01
I have installed several versions of Ubuntu Jaunty on a second hard drive in my computer (the first drive is Ubuntu Intrepid).  Most recently the Alpha 6 and then the Beta.  A good while back (maybe around Alpha 4 or so), I had edited the applications menu to add a terminal icon with the command "gksudo gnome-terminal", and a "gksudo gedit" command.  Both of these commands worked fine until a couple of weeks ago (or so).  I don't remember if it was with A6 or the beta, but the "gksudo gnome-terminal" command doesn't work any more.  The first time I click on the icon after a fresh boot, I will get a prompt for root password.  When I enter the password . . .poof.  It's just gone.  After the first time I click on the icon, absolutely nothing visible happens.  The  "gksudo gedit" still works as expected.  

If I open a normal terminal window and enter "gksudo gnome-terminal", nothing at all happens there either.  And as far as I know, these commands still work on the Intrepid install.  I say that because I have not booted the Intrepid install for a while since Jaunty is working well for me.


Any ideas???

TIA,

xeddog

---

### Post by simtaalo on 2009-04-01
not sure why it doesn't work but you should use gksu instead of gksudo

---

### Post by xeddog on 2009-04-01
Tried gksu instead of gksudo and get the exact same thing.  

Thanks,

xeddog

---

