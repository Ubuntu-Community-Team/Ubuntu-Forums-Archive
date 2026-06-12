---
title: "Found a bug"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Losik on 2009-10-11
I guess I've found a bug in Karmic but I dont know how to submit it properly.
Wen I press ctrl+alt+l there is a window asking the password. But when my friend typed a password randomly for about 5 -10 times he entered in. I've checked it several times myself typing "asdfgh" (it is not my password) and every time on the 6th or 7th try I entered.
After this ctrl+alt+l doesn't work until reboot.
Check it on your computers and if you have the same problem please rebort a bug.

---

### Post by damis648 on 2009-10-11
Works fine here. In fact, after five tries, it should go back to the screensaver.

---

### Post by cariboo on 2009-10-11
Post a question in [Karmic Koala Testing & Discussion]("http://ubuntuforums.org/forumdisplay.php?f=359") to see if anyone else has the same problem, if no-one has, press Alt-F2 and type:

```
ubuntu-bug <packagename>
```

where <packagename> is the name of the package you are having a problem with.

---

### Post by bapoumba on 2009-10-12
Moved to karmic.

---

### Post by themusicalduck on 2009-10-12
Hmm, tried it, and this seems to happen for me as well.

---

### Post by Jay_Bee on 2009-10-12
Wow, this one is nasty.
Reported, please confirm: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/449873](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/449873)

---

### Post by bapoumba on 2009-10-12
I marked it as affecting me too. Took more than 6 times though, but I used only 2 letters : "mm"

---

### Post by emarkay on 2009-10-12
That's the screensaver app, and on the 5th nonsense password, I get the screensaver for a second or two, but nothing more.

---

### Post by cariboo on 2009-10-12
+1, I tried the op's method and got dropped to a screensaver after the 5th try, and started all over again for a second 5 tries and no luck, I couldn't log in.

---

### Post by Longinus00 on 2009-10-12
> **cariboo907 said:**
> +1, I tried the op's method and got dropped to a screensaver after the 5th try, and started all over again for a second 5 tries and no luck, I couldn't log in.

It didn't work for me until I typed in the same thing each time (this might be coincidental). Try it again?

---

