---
title: "question about ctrl+alt+f1, ctrl+alt+f7, ctrl+alt+f8"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Scott82 on 2010-04-04
ok, i know the basics, that (gonna call ctrl+alt x for this 'cuz i don't wanna have to type them over and over) x+f1 takes you to a command prompt (think you have to log in first) and x+f7 and x+f8 normally take you back to GUI, but i dono what the difference is between f7 and f8.... reason i'm wondering is currently, x+f7 doesnt work on my pc right now and i thought it was the one normally used.... it takes me to a screen that repeatedly says cannot write to broken pipe or something like that. x+f8 seems to be fine though, so i'm mostly just wondering what the difference is.

edit:: hmm, maybe i was just going nuts last night 'cuz now x+f7 works and x+f8 does nothing...... i dono.

---

### Post by ajgreeny on 2010-04-04
Ctrl+Alt+F8 would normally do nothing, as is now happening for you.

You would only see an F8 desktop if you login again to a gui without logging out of the original.  At least, I think that's the case.

---

### Post by emarkay on 2010-04-04
Guess we need a link to the official keyboard "shortcuts" for Lucid...

---

### Post by gare on 2010-04-04
documentation? bah!!

---

### Post by Longinus00 on 2010-04-04
[http://www.x.org/archive/X11R6.8.0/doc/Xorg.1.html#sect7](http://www.x.org/archive/X11R6.8.0/doc/Xorg.1.html#sect7)

---

### Post by emarkay on 2010-04-04
> **gare said:**
> documentation? bah!!

Humbug...  :) 



Longinus00, Thanks!  Will X11R6.8.0 be the version in the final Lucid X?

---

### Post by grandsatrap on 2010-04-04
On my laptop, CTRL-ALT-F1 to F6 are different tty logins. They all seem to be just to a command prompt. If I exit one of them then it takes me back automatically to CTRL-ALT-F7 - my main GUI one.

CTRL-ALT-F1 shows the boot messages (the ones that haven't scrolled off the screen)

CTRL-ALT-F8 also shows messages on my computer. These show up when I switch from AC to Battery and vice versa. It doesn't always work though. 

When I switched users to a guest user, this showed up as CTRL-ALT-F9. I can leave this user on, with Firefox ... and the process is still running and taking up CPU time. After I log off the guest user, CTRL-ALT-F9 just becomes a blank screen, like F10-F12.

---

### Post by Longinus00 on 2010-04-05
> **emarkay said:**
> Humbug...  :) 



Longinus00, Thanks!  Will X11R6.8.0 be the version in the final Lucid X?

```
$ X -version
```

---

