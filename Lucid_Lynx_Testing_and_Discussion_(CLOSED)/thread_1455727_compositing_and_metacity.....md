---
title: "compositing and metacity...."
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sparkus on 2010-04-16
Just a real quick simple question.

I've been having some issues with the min/max/close buttons on lucid, and finally managed to make those work with metacity --replace.

But I'm also having issues with compositing being disabled, and docky REALLY doesn't like that.

metacity says compositing is enabled...but docky doesn't seem to believe it.

anybody ran into similar issues?

Thanks in advance.

---

### Post by Owen.C93 on 2010-04-16
> **sparkus said:**
> Just a real quick simple question.

I've been having some issues with the min/max/close buttons on lucid, and finally managed to make those work with metacity --replace.

But I'm also having issues with compositing being disabled, and docky REALLY doesn't like that.

metacity says compositing is enabled...but docky doesn't seem to believe it.

anybody ran into similar issues?

Thanks in advance.
I just put it as an start up application.

Go-preferences-startup applications and then add

Name :Compositing Manager
Command: xcompmgr
Coment: whatever you like :)

---

### Post by sparkus on 2010-04-16
> **Owen.C93 said:**
> I just put it as an start up application.

Go-preferences-startup applications and then add

Name :Compositing Manager
Command: xcompmgr
Coment: whatever you like :)
hmmm, that's an easy solution, as xcompmgr wasn't installed for some reason! doh!

Thank you very much!

---

### Post by dalonso on 2010-04-16
> **sparkus said:**
> hmmm, that's an easy solution, as xcompmgr wasn't installed for some reason! doh!

As far as I know, Metacity has its own composition manager embedded and you should not need to install xcompmgr, that's the reason for it not being installed by default.

---

### Post by seeker5528 on 2010-04-16
> **sparkus said:**
> metacity says compositing is enabled...but docky doesn't seem to believe it.

anybody ran into similar issues?


Works fine for me.

I don't know what you mean when you say "metacity says compositing is enabled".

As far as I know the only way to enable/disable the compositing in Metacity is to open the gconf-editor and go to 'apps --> metacity --> general' and check/uncheck the box next to 'Compositing_Manager'. And I don't know anywhere else where it would show you that it is enabled either.

Later, Seeker

---

