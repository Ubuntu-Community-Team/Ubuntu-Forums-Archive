---
title: "login, black screen then back to login screen"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by carpetbelly on 2009-09-11
I have a spare lappy I put 9.10 on, well, it had 9.04 clean fresh install I upgaded to 9.10 and now I seem to be stuck in an infinate loop of the above. Where I log in, screen goes black then back to the log in screen. I've done a search, but not had any luck thus far.

---

### Post by dreddor on 2009-09-11
I had the same problem.

I hit Ctrl + Alt + F1 to get my terminal.

I logged in and killed gdm.

```
ps ax | grep "gdm"
```

I found the PID of the gdm process and killed it.

```
sudo kill -9 [PID]
```

I could then log in. That help?

---

### Post by Roswellgrey on 2009-09-11
ATI video card in the lappy ??  If so, this might help ...

  
[http://ubuntuforums.org/showthread.php?t=1255442&highlight=ati+karmic&page=2&post=11](http://ubuntuforums.org/showthread.php?t=1255442&highlight=ati+karmic&page=2&post=11)

---

### Post by carpetbelly on 2009-09-11
thanks for the info... yes, there's an ati card in the lappy
I'll give that a go when I get home, something rings a bell with that. I'll report back here when I've done that and fingers crossed we can put this down as solved so I can refer back to this another time when I've forgotten the same thing lol

---

### Post by vs8 on 2009-09-11
I have a similar problem. My lappy also has an ATI card. The thing is that I installed KDE 4.3 just to play with it, but I let KDM to be the default login manager. When I switched back to GDM and restarted the pc the login screen was black, after pressing any key the command line appears. I log in but still in the same interface, so I "sudo gdm" and GDM starts normally and then I can use the GUI.

Strange isn't it?

---

### Post by carpetbelly on 2009-09-11
brilliant, thanks very much for that... works a treat now.

---

### Post by Roswellgrey on 2009-09-12
Excellent :)  Kudos to tsger for posting the howto - it got me out of the same situation a couple of days ago ...

---

