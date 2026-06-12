---
title: "Can't update,"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by psychok9 on 2009-02-10
After a lot of problem with Jaunty and the last dmraid bugged (i'm using dmraid_1.0.0.rc14), now I have this problem:

[[IMG]http://img17.imageshack.us/img17/9862/errorzw8.th.png[/IMG]](http://img17.imageshack.us/my.php?image=errorzw8.png)

I've locked only dmraid_1.0.0.rc14 because the new rc15 version don't found my Intel Raid array... but I don't if the Synaptic problem can't update for the package rc14 or others problem.

---

### Post by taavikko on 2009-02-10
Only few people speak italian, so translated output would be nice:)

```
LANG=C sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by psychok9 on 2009-02-10
> **taavikko said:**
> Only few people speak italian, so translated output would be nice:)

```
LANG=C sudo apt-get update && sudo apt-get dist-upgrade
```

Sorry for mixed language message! I don't see it because often I got this lol mixed messages.
Fortunately this problem is Canonical related and **solved**! (or I've fixed without know how XD).
Now I can update without problems.:guitar:

Thank you for the tip :) I save it.

---

### Post by Nixie Pixel on 2009-02-11
It looks similar to a problem I am having, please see the screenshot below for details - perhaps the two problems are the same?

[IMG]http://nixiepixel.com/images/misc/updateproblem.jpg[/IMG]

---

### Post by Nullack on 2009-02-11
Nixie that was caused by the alpha repos needing fixed up dependencies. Are you hitting the main server for sources? Sometimes the mirrors are slow from main. Grab main, do an update and youll be good.

---

### Post by Nixie Pixel on 2009-02-11
Nope, main is very slow for me.  Believe it or not the best server for me is in New Zealand.

I added Main and got the update, no more error message.  Thanks for the tip!

---

