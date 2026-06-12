---
title: "How to disable Ubuntu One?"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jackhynes on 2009-08-08
Every time I disable Ubuntu One in Accessories > Startup Applications it seems to start again after every restart. 

Does it enable itself at startup after every update or is there another reason?

---

### Post by frustphil on 2009-08-08
Just purge it. 

> sudo apt-get purge gnome-ubuntuone-client

---

### Post by jackhynes on 2009-08-08
Thanks, probably the best plan. Although the package name is actually ubuntuone-client-gnome.

---

### Post by xebian on 2009-08-08
> **jackhynes said:**
> Thanks, probably the best plan. Although the package name is actually ubuntuone-client-gnome.

Oh boy.  I'd better flag -kde should there be one coming.  :(

---

### Post by Martje_001 on 2009-08-08
Is it installed by default in Karmic? And even automatically started?

If it is: that's just plain WRONG.

---

### Post by rudenko_ruslan on 2009-08-08
> **Martje_001 said:**
> Is it installed by default in Karmic? And even automatically started?

If it is: that's just plain WRONG.
Installed - yes, but it will not automatically start until you click on "Ubuntu One" (Applications > Internet > Ubuntu One) and configure it.

---

