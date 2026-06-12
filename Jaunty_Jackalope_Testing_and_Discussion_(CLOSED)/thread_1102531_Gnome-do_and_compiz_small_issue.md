---
title: "Gnome-do and compiz small issue"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-03-21
When I start Gnome I have automatically set gnome-do and compiz in the startup applications list; I set gnome-do in the appearance as glass interface but when I logon again the appearance goes to classic saying that I have to set a compisiting window manager (in the meanwhile compiz runs fine); seems to me that gnome-do starts before compiz in the startup applications.
I've tried to change the string in the gnome-do launcher in this way:
> sleep 10 && gnome-do&
but without luck (gnome-do does not start at all).

Anyone have this issue too or any suggestions for this?

---

### Post by zekopeko on 2009-03-21
i just ticked the box in gnome-do preferences for do to autostart. but i'm using docky.
simply report a bug if it still misbehaves.

---

### Post by Cenotaph on 2009-03-21
running compiz as a startup applications isn't ideal, because he loads metacity first and only later he runs compiz.

I used to have this same issue in arch when running docky and never solved it. in ubuntu though, if u select normal or extra effects in appearance he will set compiz as gnome's window manager properly and it should be ok then

---

### Post by dentaku65 on 2009-03-22
> **Cenotaph said:**
> running compiz as a startup applications isn't ideal, because he loads metacity first and only later he runs compiz.

I used to have this same issue in arch when running docky and never solved it. in ubuntu though, if u select normal or extra effects in appearance he will set compiz as gnome's window manager properly and it should be ok then

Well compiz loads in the start up applications because I've set normal in the appearance of Gnome I supposed, I did not put directly in the startup apps compiz...

---

