---
title: "Tilda"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sgosnell on 2009-10-09
Anybody else having problems getting Tilda to run?  I've been using it for a long time, and I love having a terminal available via a hotkey.  On Karmic, though, it crashes every time it tries to run.

---

### Post by nikolaidis on 2009-10-09
Yup. It segfaults every time I try to run it. I was able to launch it the first time, to configure it, but not after that.

---

### Post by jcris on 2009-10-09
Same here...was waiting to see if any of the updates fix it.

---

### Post by lovinglinux on 2009-10-09
Same here.

---

### Post by slakkie on 2009-10-09
So, who will create the bugreport?

---

### Post by chrisccoulson on 2009-10-09
No need
```
tilda (0.09.6-1ubuntu1) karmic; urgency=low

  * debian/patches/03_gtk_window_realize.dpatch:
    - Create GDK resources before trying to access them. Fixes a crash
      on start (LP: #406295)

 -- Chris Coulson <chrisccoulson@ubuntu.com>  Fri, 09 Oct 2009 18:06:58 +0100

```

---

### Post by unique on 2009-10-09
Give Guake a try...  in the repo

---

### Post by pelle.k on 2009-10-09
May i suggest trying Guake, or stjerm perhaps? stjerm may be a better fit for lightweight setups though.

---

### Post by sgosnell on 2009-10-09
OK, I'll take a look at them.  Thanks for the pointers.

---

### Post by sgosnell on 2009-10-13
Well, I still prefer Tilda.  Stjerm doesn't take the focus when it's invoked, so you have to click in it before you can start typing.  PITA.  Guake is ugly, and I can't find a way to modify the size, so that it doesn't take up the entire width of the screen.  There is an update to Tilda, though, that supposedly fixes the problem, but that update also broke Karmic for me, and it won't even boot now.  I wiped the SDHC I had it on, and probably will wait for the full release, and maybe even awhile after that.  Karmic isn't looking all the promising for now.

---

### Post by tlacuache on 2009-10-13
I use stjerm, and you can actually get it to take focus when you hit the shortcut. However, if you're runing Compiz, I think Compiz is what's actually preventing it from stealing focus. You can fix this easily in the "CompizConfig Settings Manager" in your preferences:

1. run "CompizConfig Settings Manager"
2. click "General Options"
3. go to the "Focus & Raise Behevior"
4. Change the value for "Focus Prevention Windows" to:
```
any & !(title=stjerm)
```

Anyway, that's what worked for me.

---

### Post by pelle.k on 2009-10-13
> However, if you're runing Compiz, I think Compiz is what's actually preventing it from stealing focus.
It is. Stjerm works great using metacity (with or without compositioning), or any other WM.
> Guake is ugly, and I can't find a way to modify the size, so that it doesn't take up the entire width of the screen.
There's not very much to look at, so if that little you can see is ugly, then so be it :) And you are right, you can't set the width of guake.
It is in active development though, while tilda seems very on and off in that regard. Latest tilda update was Apr 28 2008.

---

### Post by sgosnell on 2009-10-14
I'm using metacity, but I'll try the compiz settings and see what happens.  It appears perhaps Tilda is being maintained, at least the update came along from somebody.

---

### Post by pelle.k on 2009-10-14
> It appears perhaps Tilda is being maintained, at least the update came along from somebody.
Probably the debian/ubuntu/red hat maintaners, doing some unofficial patching to keep it up to date. Which is good :)

---

