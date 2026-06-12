---
title: "Best way to start gnome-shell ?"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2009-10-01
I'd like to try living with gnome-shell for a while.  When I run it from a console after my gnome session has already started, it gives this error:

"Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager."

I can certainly use the "--replace" option, but what's the intended way for people to use it?  Is there some config file I'm supposed to slip this command into, so that gnome-shell is the initial window manager for display :0.0 , rather than gnome-shell having to replace whatever window manager is *initially* serving that display?

---

### Post by blakamin on 2009-10-01
great tutorial here
[OMG! UBUNTU!]("http://d0od.blogspot.com/2009/09/how-install-gnome-shell-intrepid-jaunty.html")


```
gnome-shell --replace
```

---

### Post by christian.convey on 2009-10-01
> **blakamin said:**
> great tutorial here
[OMG! UBUNTU!]("http://d0od.blogspot.com/2009/09/how-install-gnome-shell-intrepid-jaunty.html")


```
gnome-shell --replace
```
Thanks, but that still has you manually launching it from a console, using the "--replace" command-line argument.  I'm trying to figure out how to get it used from the *very beginning* of a session.

---

### Post by joey-elijah on 2009-10-01
> **christian.convey said:**
> Thanks, but that still has you manually launching it from a console, using the "--replace" command-line argument.  I'm trying to figure out how to get it used from the *very beginning* of a session.

Yikes! Why would you want to do that?! :P 

There's a quick guide here

[http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html](http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html)

---

### Post by blakamin on 2009-10-01
Sorry, misunderstood...

---

### Post by nzjrs on 2009-10-02
> **joey-elijah said:**
> Yikes! Why would you want to do that?! :P 

There's a quick guide here

[http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html](http://www.mail-archive.com/gnome-shell-list@gnome.org/msg00023.html)

I followed the instructions (changing the exec line from jhbuild to call gnome-shell directly) and it didn't work. Anyone have some success?

---

### Post by Seventh Reign on 2009-10-02
> **christian.convey said:**
> Thanks, but that still has you manually launching it from a console, using the "--replace" command-line argument.  I'm trying to figure out how to get it used from the *very beginning* of a session.


You are better off just using --replace each time you log in.  It will save you a boatload of hassle.

---

### Post by dinxter on 2009-10-02
if you use gconf-editor then change
/desktop/gnome/session/required_components/windowmanager
to the manager you want
though Seventh Reign is probably right, stick to doing it manually with --replace, gnome-shell is a work in progress

[EDIT] if you find yourself having trouble changing back, the key is mirrored in ~/.gconf so you can edit it from the console

---

