---
title: "Shadow remains on desktop, anyone else have this?"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-10-16
As the pic shows, after opening and closing the drawer it's shadow remains.

---

### Post by oboedad55 on 2009-10-16
> **mdurham said:**
> As the pic shows, after opening and closing the drawer it's shadow remains.

Which version of Ubuntu are you using, is it the UNR?

---

### Post by Nate8nate on 2009-10-16
I'm having this with the calendar in Karmic, too.

---

### Post by mdurham on 2009-10-16
> **oboedad55 said:**
> Which version of Ubuntu are you using, is it the UNR?

I'm using Ubuntu Beta 386, I dunno what UNR is?

---

### Post by mdurham on 2009-10-16
> **Nate8nate said:**
> I'm having this with the calendar in Karmic, too.
It's strange but I don't get it with the clock/calendar or anything else as far as I know.

---

### Post by drs305 on 2009-10-16
mdurham,

If you aren't using Compiz, the shadow effect is probably being created by metacity. See if "compositing" is turned on. Composting is the effect which produces the shadows. If it's on, turn it off and see if the shadows are still there. 

It would still be a bug, but at least you would know what's causing it.

```

gconf-editor /apps/metacity/general/compositing_manager

```

Added: Submitted prior to seeing previous post. I would expect metacity to effect more than just one applet.

---

### Post by mdurham on 2009-10-17
[QUOTE=drs305;8117277]
```

gconf-editor /apps/metacity/general/compositing_manager

```

/apps/metacity/general/compositing_manager is OFF

Very strange!

---

### Post by forumache on 2009-10-17
> **mdurham said:**
> It's strange but I don't get it with the clock/calendar or anything else as far as I know.

Calendar is OK. It was a fixed compiz bug.
Investor Applet is not ok. Bug reported. Try to add Investor applet if you want to see shadows :)

---

### Post by forumache on 2009-10-17
> **Nate8nate said:**
> I'm having this with the calendar in Karmic, too.

Maybe you did not update recently? It was a bug with compiz, but it was fixed.

---

### Post by mdurham on 2009-10-17
> **forumache said:**
> Calendar is OK. It was a fixed compiz bug.
Investor Applet is not ok. Bug reported. Try to add Investor applet if you want to see shadows :)

Yes, I didn't notice that one. Interestingly it behaves differently from the drawer, I can erase the remaining drawer shadow with another window but it doesn't work with the Investor shadow.

forumache, I'm fully up-to-date.

---

### Post by FrancoNero on 2009-10-17
had this also, but not since the latest bunch of updates. aptitude update and aptitude safe-upgrade will do the trick I think

---

### Post by Nate8nate on 2009-10-18
I'm still having this on the calendar, even on an up-to-date system.

---

### Post by mdurham on 2009-10-19
> **FrancoNero said:**
> aptitude update and aptitude safe-upgrade will do the trick I think
I think not!

---

