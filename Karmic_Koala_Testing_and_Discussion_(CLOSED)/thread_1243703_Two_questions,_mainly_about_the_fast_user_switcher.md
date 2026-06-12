---
title: "Two questions, mainly about the fast user switcher"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-08-18
In Jaunty (or Intrepid, don't remember) there was a change introduced that made it possible to shut down or restart the computer from the userswitchermenu in a very easy way. Now I see that this has changed to the worse in Karmic, hope it is temporary. We are now using one place to shutdown in the systemmenu and one in the switcherapplet (or that is only to log out?) To summarize it, things has been made far more userunfriendly.

Secondly, there is a big regression in Karmic, you can't set your status in the default IM-client from the userswitcher anymore, will this be fixed?

---

### Post by jpeddicord on 2009-08-18
If I remember right, that's because that's not the fast user switch applet. I believe it was replaced with a GNOME applet because the original package hasn't yet been updated to work with GDM 2.27. See the [fast-user-switch-applet]("apt:fast-user-switch-applet") package; at the moment it cannot be installed. LP #[lpbug]395298[/lpbug].

---

### Post by Locke_99GS on 2009-08-18
Using *gconf-editor*, alter FUSA's configuration using the keys at */apps/fast-user-switch-applet*.

edit: I suppose I should be giving advise from within Karmic - oops. Disregard, then.

---

### Post by olskar on 2009-08-19
> **jacobmp92 said:**
> If I remember right, that's because that's not the fast user switch applet. I believe it was replaced with a GNOME applet because the original package hasn't yet been updated to work with GDM 2.27. See the [fast-user-switch-applet]("apt:fast-user-switch-applet") package; at the moment it cannot be installed. LP #[lpbug]395298[/lpbug].

Thanks, that explains it. 

But > this is being actively worked and will land in the coming weeks :)

---

### Post by chrisccoulson on 2009-08-19
> **olskar said:**
> Thanks, that explains it. 

But  :)

You can already install what is being worked on:

```
sudo apt-get install indicator-sus
```

---

### Post by rudenko_ruslan on 2009-08-19
Huh, indicator-sus? What is that? Will this thing be installed in Karmic on default in future? Or it's just a replacement for FUSA?

---

### Post by olskar on 2009-08-27
Has this regression been fixed? Anyone knows?

---

### Post by jpeddicord on 2009-08-27
indicator-applet-session replaces the functionality in fusa (and maybe the indicator applet itself, I haven't figured that out).

---

