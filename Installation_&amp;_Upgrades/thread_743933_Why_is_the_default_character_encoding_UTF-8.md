---
title: "Why is the default character encoding UTF-8?"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by discorsage on 2008-04-03
Does anyone know why the default encoding is UTF-8?  This seems like a not-so-friendly encoding.  A simple 'é' ends up looking strange in terminal windows.  I've noticed that debian by default does not do this - why does ubuntu?  Are there any dangers in changing to something else?

To get characters to display correctly, I've had to change

/etc/default/locale

LANG="en_US.UTF-8"

to

LANG="en_US"

---

### Post by luisromangz on 2008-04-03
Using unicode is the way to go. I know that this can be a problem with certain programs, but we should have been using Unicode for a long time.

---

